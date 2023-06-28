# ActionScript

## Function Bodies and Arrow Functions

```
function process(...arguments : [Number]) : [Number] (
    arguments.map(a => a + 1)
);
```

## Destructuring

```
for each (var [k, v] in mapObject) {
    //
}
```

## Type Inference, Variable Scope and Shadowing

VioletScript example:

```
{
    var a : Number = 10;
    var a : String = a.toString(); // re-define 'a'

    var b = 10;
    {
        var b = 15;
    }
    trace(b); // 10

    var c = ''; // c : String
}
```

## Enums

Flags enums are covered in other sections.

```
enum ProductCategory {
    FOOD;
    ELECTRONIC;
}

type SearchOptions = {
    category : ProductCategory,
};

function searchProducts(options:SearchOptions):Promise.<String> {
    //
}

const searchResults = await searchProducts({
    category: 'electronix',
        //    ^ VerifyError! Undefined variant 'electronix'
        //                   Meant 'electronic'?
});
```

## Markup

```
var c:p.q.Container = <p.q.Container><p.q.Option checked/></p.q.Container>;
```

## Decorators

Brackets prefixes on annotatable definitions are called decorators, not meta-data.

## Item Alias and Namespaces

VioletScript discards qualified names and uses the context keyword `namespace` with different effects.

```
import Qf = q.f.*;

type Ta = To;

namespace No {}
namespace Na = No;
```

## Generics

```
class C.<T> {}

type B.<T> where T:IDisposable = A;
```

## Reflection

VioletScript example:

```
o.x;    // property operator
o[k];   // indexing operator (not property operator)
```

## Structural Types

VioletScript has several structural types.

## Proxies

VioletScript proxies allow to override language operations.

## Embedding Media

```
// application/text

var str : String = embed './data.txt';

// application/octet-stream

var ba : ByteArray = embed './data.bin';
```

## Asynchrony

```
function af():Promise.<Number> {
    await another();
    return 10;
}
```

## Type Testing

VioletScript example:

```
switch type (v) {
    case (d : Date) {
    }
    default {
    }
}

if (v is p : Point && p.x > 50) {
    // p : Point
}
```

## Keywords Not Reserved in Certain Contexts

a) VioletScript example:

```
promise.catch(...);
```

b) VioletScript example:

```
function #try():void {
}
```

## Generators

```
function g():Number {
    yield 10;
}
var it = g();
it.next(); // { done: false, value: 10 }
it.next(); // { done: true, value: undefined }
```

## Optional Access

```
o?.x;
o?.[k];
o?.(arguments);
```

## Include Directive

`include` supports source locations.

```
<!-- foo.vs -->

class C {
    include './foo.impl.vs';
}

<!-- foo.impl.vs -->

function C() {
    super();
}
```

It is also important to remember to exclude the included source from the compiler options (in this case `foo.impl.vs`).

## Use Resource

```
use resource (fileStream = new FileStream()) {
    fileStream.open(file);
}
```

## Script Meta Data

```
// current script URL
import.meta.url

import.meta.env.VAR_NAME
```

## Array and Object Initializers

Object and array initializers are more flexible in VioletScript.