# User Value Types

Value classes are passed by value. They can be defined by using the special `Value` decorator, as follows:

```
[Value]
class V {
	const x: Number;
	const y: Number;
}
```

Fields are all read-only. You can re-assign a field from an existing instance like this:

```
o = { x: newValue, ...o };
```