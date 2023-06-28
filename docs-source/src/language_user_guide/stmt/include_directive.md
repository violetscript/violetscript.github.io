# Include Directive

Combines statement sequence from a script with the current statement sequence.

```
include './anotherScript';
```

This also allows for partially implementing classes, similiar to C#'s `partial` classes. For example:

```
class C {
    var x: Number = 10;

    include './foo';
}
```

foo.vs:

```
function f(): void {
    trace(this.x);
}
```

## Path resolution

- You do not need to specify the `.vs` extension.
- You do not need to specify `index.vs` when resolving to a directory.

```
// if './core' is a directory, the following lines
// are equivalent:
include './core';
include './core/index.vs';
```

## Packages

It is allowed to define packages in an included script as long as it is included from a top-level context:

```
// foo.vs
include './bar';

// bar.vs
package q.b;
```

## Visibility

`include` inherits the scope from where it is included.

```
// foo.vs
include './bar';

class C {
}

// bar.vs
var x: C?;
```