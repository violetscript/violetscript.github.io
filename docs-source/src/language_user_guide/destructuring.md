# Destructuring

## Array Destructuring

Array destructuring syntax can in addition be used for tuples and user proxies.

```
[x, y] = someArray;
```

## Record Destructuring

```
({x} = someObject);
```

## Non-null assertion

You may get a verify error when destructuring from something that contains `undefined` or `null`. You can use exclamation (`!`) to assert the base is non-null and non-undefined:

```
const [{x!: {y}}!]! = o;
```