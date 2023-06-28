# Decorators

A decorator is a function that either returns `void` or returns another function that returns `void`, applied to either a type, property or method as expressions enclosed by square brackets. Decorators cannot be applied everywhere.

`[D(x = 10)]` is equivalent to `[D({x: 10})]`.

Note that 4 lexical names may be reserved in some contexts. Jump to the _Reserved Lexical Decorators_ section below for quick information.

## Decorators Applied to Types

```
function MyTypeDecorator(type: Class): void {
}

[MyTypeDecorator]
class C {
}
```

## Decorators Applied to Properties

```
function MyFieldDecorator(o: C, {name}: Binding): void {
    trace(name);
}

class C {
    [MyFieldDecorator]
    public var x: Number;
}
```

## Decorators Applied to Methods

```
function MyMethodDecorator(o: C, name: String): void {
    trace(name);
}

class C {
    [MyMethodDecorator]
    public function f(): void {
    }
}
```

## Reserved Lexical Decorators

The following decorators are reserved, but can still be used if they do not directly appear as lexical references:

- `[Metadata()]`
- `[Allow()]`
- `[Warn()]`
- `[FFI()]`
- When applied to a class definition, `[Value]` is reserved
- When applied to a class definition, `[DontInit]` is reserved
- When applied to an enum definition, `[Flags]` is reserved

You can still use them if they are under a namespace or package, such as `q.b.Metadata`.