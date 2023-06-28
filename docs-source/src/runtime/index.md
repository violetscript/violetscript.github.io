# Runtime

This section lists some runtime details and general optimizations.

## Single Item Insertion

The following call takes only one argument, so do not create an throwaway `Array` for rest arguments:

```
array.push(v);
```

## Constant Number Iteration

The following can be optimized by skipping the creation of the `Generator` instance and skipping handling the step parameter.

```
for each (var i in Number.range(0, 10)) {
    // procedure
}
```

## String Representation

`String` is either original or a slice of another one. When the type is auto boxed, this is not the case.

## Auto Boxing of Value Types

Value types are interned on auto boxing. Primitive types like `Number` are interned in more depth, for example, values under < 512 are looked up into a particular collection, `String`s are divided into collections by length and `Boolean` is simply binary. These internation collections should preferably consist of weak references whenever possible in the host environment.

## Any Type Representation

- In native host environments, for the `*` type, a `undefined` value is identified by variant 0, `null` by variant 1 and anything else is an actual `Object` reference address.

## Union Type Representation

Union types are structural, however they are differentiated by member order. The first variant starts by the number 0.

```
// undefined = 0
// RegExp = 1
type UoR = undefined | RegExp;

// RegExp = 0
// undefined = 1
type RoU = RegExp | undefined;
```

## Math methods

Things like `min()`, `max()` and `clamp()` can be optimized according to given arguments.

- `min()` with 2 arguments
  - Specialized types
- `max()` with 2 arguments
  - Specialized types
- `clamp()` with specialized types