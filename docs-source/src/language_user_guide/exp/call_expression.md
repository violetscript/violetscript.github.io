# Call Expression

Call expression is indentation-aware.

```
f();

// optional call in case f is undefined or null
f?.();
```

## Special Behavior

- If `f` is an enumeration, the call expression corresponds to a forced conversion from either String or numeric value to the enumeration.
- If `f` is a type, but not an enumeration, it corresponds to the use of the `new` operator.
  - If `f` is the String type, it corresponds to a string conversion.

```
E(v)
T(ctorArguments)
String(v) // string conversion
```