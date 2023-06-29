# Quick Tour

## Why

VioletScript is a faster version of JavaScript efficient as C# or Java.

## Status

- Type checker is done.
- Codegen is not yet done. It'll target either WebAssembly or C++.

## Basics

```
trace('Hi!')

var x: Number = 0

var y = 0 // y: Number

const z = 0

var w: * = undefined // '*' is the any type

function f1(): Number {
    return Infinity
}

function f2(): Number (
    Infinity
);

// you can shadow variables
function shadowing(): void {
    'use shadowing'
    const x = false
    const x = ''
}

function typeSystem(): void {
    const array: [Number] = []

    const tuple: [String, Boolean] = ['', false]

    const union: Number | undefined | null = null

    const nullable: null | Boolean

    const nullable: Boolean? // equivalent to previous constant

    // records are immutable structures
    const record: {x: Number, y: Number} = {x: 10, y: 10}

    // the following have equivalent types
    const record: {x?: Number} = {};
    const record: {x: undefined | Number} = {};

    // as you saw above, a record field is optional
    // when it can contain undefined.

    // function types
    const fn: (...arguments: [Number]) => void = () => {}
}

type D = Decimal;

function nullability(): void {
    // asserts that `o` is non-null and non-undefined;
    // returns a type without undefined and null.
    o!

    // optional chaining
    o?.x.y?.z?.[i]?.()
    a?.[i]
    f.()
}
```

## Enums

An enum is an object...

- represented in memory as a primitive number;
- whose possible variants are associated with...
  - an unique user friendly string and
  - an unique number;
- that can define custom properties;
- that, where expected, a variant can omit its name through a string literal;

```
enum E {
    X;
    Y = 'y';
    Z = ['z', 10];

    function f(): void {
        trace(this.valueOf());
    }
}

const e: E = 'x';
e.f(); // 0
e.valueOf() // 0
e.toString() // 'x'

const e: E = 0 // ERROR! number must be
// explicitly converted

const e: E = 'inexistent'; // ERROR! doesn't exist
```

Note that the default user friendly string is a conversion from `SCREAMING_SNAKE_CASE` (constant name) to `screamingSnakeCase`.

## Flags

Flags enums have many methods by default, such as `toggle()` and `filter()`.

```
[Flags]
enum F { X; Y; Z; }

const f: F = ['x'];
const f: F = {x: true};
const f: F = f.toggle('x');
trace('x' in f);
trace('x' not in f);
```

## Classes

```
// generic class
class C.<T> {
    var x: T

    // constructor
    function C(x: T) {
        this.x = x
    }

    // the type `T!` can be used to remove
    // any undefined and null from the parameter type.
}
```

## Packages and Namespaces

```
// shares items to all scripts.
package q.f {
    public const someString = 'violetscript'
}

import q.f.*;
import q.f.someString;

// block brackets are optional
package q.b;

// a namespace acts as a simple container for
// other items.
namespace Q {
    class C {
    }

    // define a function using the reserved word 'for'.
    // use '#' to escape a reserved word.
    function #for(x: Number): Number (
        x + 10
    );
}

Q.for(10);
```

## Type Testing

```
function typeTesting(): void {
    if (animal is falcon: Falcon && falcon.name.startsWith('F')) {
        // falcon: Falcon
    }

    switch type (object) {
        case (long: Long) {
            // Long
        }
        default {
            // anything else
        }
    }
}
```

## Destructuring

```
const {} = o
const [a] = o

// use '!' to assert non-null
// and non-undefined
const [a!] = a
const {x!: {}} = o

({} = o); // destructuring assignment
```

## Include

Use `include` to:

- Fragment a class into multiple files.
- Specifying the initialization order of static properties by including scripts in the wished order.

```
include './anotherScript';
```

## Properties

`o.x` and `o['x']` are not the same thing as in ECMAScript. `o.x` and `Reflect.get(o, 'x')` are equivalent.

## Equality

Auto-boxed types do not lose equality.

```
var x: Object = 0;
var y: Object = 0;
assert(x == y);
```

## Decorators

```
[D]
class C {
}
```

Note that six lexical decorator names are reserved in different contexts.

- `Flags` is reserved for `enum`
- `Value` is reserved for `class`
- `DontInit` is reserved for `clas`
- `Metadata` is always reserved
- `Allow` is always reserved
- `Warn` is always reserved
- `FFI` is always reserved

You can still use these decorator names if they're in a namespace or package:

```
[q.b.Metadata]
class C {
}
```

## Markup

A class must implement `IMarkupContainer` for supporting children in markup.

```
// equivalent
var o = new C
o.x = Infinity
var o = <C x={Infinity}/>
```

Markup syntax is not based on XML and cannot contain text directly. There are different ways of adding text:

```
<Container><Text text='Some text'/></Container>
// if child type can be string
<Container>{['Some text', 'Another text']}</Container>
```

## Primitive Types

- `Boolean`
- `String`
- `Number`
- `Decimal`
- `Byte`
- `Short`
- `Int`
- `Long`
- `BigInt`

## Code Safety

- Assignments are only allowed in proper contexts, otherwise that would lead to productivity issues.
- You will use the `!` operator very often, including in destructuring, for asserting that a base is not `undefined` and `null`.