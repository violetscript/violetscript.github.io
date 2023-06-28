# Nullability

The following line aliases the _dynamic_ type (\*):

```
type UndefinedOrNullOrObject = *;
```

The following line aliases the Object type:

```
type ObjectNotUndefinedNorNull = Object;
```

The following line escapes _o_ from either null or undefined:

```
o!
```

The following line escapes _T_ from union with null and undefined:

```
type NonNullT = T!;
```

## Unifying type with null

The following line:

```
type NullableT = T?;
```

is equivalent to:

```
type NullableT = null | T;
```

It can also be wrote with a `?` prefix:

```
type NullableT = ?T;
```

## Unifying type with undefined

```
type UndefinedOrT = undefined | T;
```