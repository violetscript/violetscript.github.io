# Function Types

Function types inherit the `Function` class.

```
// parameterless
type F1 = () => void;

// with required parameter
type F2 = (a: Number) => void;

// with optional parameter
type F3 = (a?: Number) => void;

// with rest parameter
type F4 = (...a: [Number]) => void;
```

## Parameter Names

A type `(a: T) => void` differs from a type `(_: T) => void` because the parameter names differ.