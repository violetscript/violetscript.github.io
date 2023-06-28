# Record Types

Record types are immutable structures passed by value. They are written in curly brackets. For example:

```
type R = {x: Number, y: undefined | RegExp};
```

A field is optional when it possibly contains `undefined`. The following types are equivalent:

```
type R1 = {x?: Number};
type R2 = {x: undefined | Number};
```

## Field Order

The sequence of the record type fields is sensitive. A type `{x: X, y: Y}` differs from `{y: Y, x: X}`. This allows for organizing memory layout.