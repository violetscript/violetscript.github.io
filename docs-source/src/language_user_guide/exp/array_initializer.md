# Array Initializer

Array initializer, written in square brackets, supports ellisions, spread components (`...otherArray`) and suffix type annotation.

Array initializer can only initialize:

- `*` (instantiates a `[*]` array)
- `Array`
- `Set`
- Flags enumerations
- Tuples

## Spread

A spread component can either be a compatible `Array`, iterator or flags.

- _Flags:_ Flags type itself.
- _Any:_ Any at compile-time; at runtime it must be a compatible iterator or array, otherwise an error occurs.
- _Set:_ Iterator.
- _Array:_ Same array type or iterator.
- _Map_: Unallowed.