# Reflection

## Constructing Types Dynamically

Use `Reflect.construct()` to construct a type dynamically, rather than `new`:

```
const c = SomeClass;
const o = Reflect.construct(c, [firstArgument]);
```

## Type Inspection

Use `Reflect.typeOf()` to get a type meta-object. It returns one of:

- `null`
- `AnyType`
- `UndefinedType`
- `NullType`
- `ArrayType`
- `ClassType`
- `EnumType`
- `InterfaceType`
- `TypeWithArguments`
- `UnionType`
- `TupleType`
- `RecordType`
- `FunctionType`
- `TypeParameter`