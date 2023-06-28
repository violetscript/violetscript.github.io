# Union Types

```
type U = undefined | Number | Boolean;

// "|" prefix

type XoY =
    | X
    | Y
```

## Member Order

The sequence of the union members is sensitive. A type `X | Y` differs from `Y | Z`. This allows for organizing memory layout.