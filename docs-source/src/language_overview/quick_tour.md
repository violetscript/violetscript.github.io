# Quick Tour

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

type TypeAlias = Number;

function nullability(): void {
    // asserts that `o` is non-null and non-undefined;
    // returns a type without undefined and null.
    o!

    // optional chaining
    o?.x.y?.z?.[i]?.()
    a?.[i]
    f.()
}

// enums wrap a numeric type, but are powerful and
// can define custom properties.
enum E {
    X; // string is 'x', numbered 0
    Y = 'y'; // string is 'y', numbered 1
    Z = ['z', 10]; // string is 'z', numbered 10

    function f(): void {
        trace(this.valueOf());
    }
}

const e: E = 'x';
e.f(); // 0

// flags have many methods by default,
// such as toggle() and filter().

[Flags]
enum F { X; Y; Z; }

const f: F = ['x'];
const f: F = {x: true};
const f: F = f.toggle('x');
trace('x' in f);

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

// a package is used for sharing items to all
// programs.
package com.scientific {
    // note that curly brackets are optional
}

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

## Packages

```
package q.f {
    public const someString = 'violetscript';
}

import q.f.*; // or
import q.f.someString;
```

The curly brackets are optional:

```
package q.f;
public function work(): void {
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

## Include Directive and Multiple Files

The `include` directive is mainly used for two purposes:

- Fragmenting implementation of a class into multiple files.
- Specifying the static initialization order by including scripts in the wished order.

It can appear anywhere.

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

## Type Inference

As of now, function definitions either at the top-level, at a package, at a class or at a namespace won't perform signature type inference and will generate verify errors if any parameter is untyped and a warning if the return is untyped.

There are exceptions:

- Constructor doesn't need return type annotation.
- Setter followed by getter doesn't need a typed signature.
- Setter doesn't need return type annotation.

```
function get x(): Number (10);
function set x(value) {
}
```

Other than this, VioletScript will perform type inference in general for lambdas, enum variants, variable initializers, object initializers and array initializers.

In the future, it'll be possible to override methods with already resolved signature omitting its types, which is often the case for libraries:

```
class Project extends Node2D {
    override function process(delta) {
    }
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

## Code Safety

- Assignments are only allowed in proper contexts, otherwise that would lead to productivity issues.
- You will use the `!` operator very often, including in destructuring, for asserting that a base is not `undefined` and `null`.