# Index Expression

Unlike EcmaScript, the index expression, in the form `o[k]`, uses an indexing mechanism that is separate from the object properties mechanism. This resolves conflict of properties and indexes. Methods such as `Reflect.get(...)` can be used in case a property must be dynamically resolved.

The index expression is indentation-aware.

```
o[k];

// optional index in case o is undefined or null
o?.[k];
```