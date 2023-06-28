# String Type

The String type is UTF-16 encoded for compatibility with the ECMA-262 String type.

## Code Points

You can easily iterate code points over a string with `CodePointIterator`:

```
var iterator = 'v'.codePoints();
iterator.next(); // 0x76
iterator.next(); // 0 (no character)
iterator.hasRemaining; // false
```