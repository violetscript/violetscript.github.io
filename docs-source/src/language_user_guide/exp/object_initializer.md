# Object Initializer

Object initializer, written in curly brackets, supports shorthand property notation, trailling comma, spread components (`...spreadObject`) and a suffix type annotation.

Object initializer can only initialize:

- `*` (instantiates an empty `Object`, not allowing spread)
- `Map`
- Flags enumeration
- Record type
- Class without a `DontInit` decorator

Additional semantics:

- Using object initializer to initialize a plain object results in an object whose `constructor` property returns `Object`.
- Spread elements are evaluated before fields when initializing flags, record or class, that is, anything other than `Map`.