# For Statement

```
for (i; c; u)
{
	// procedure
}
for (var i; c; u)
{
	// procedure
}
for (var i in o)
{
	// procedure
}
for (i in o)
{
	// procedure
}
for each (var i in o)
{
	// procedure
}
for each (i in o)
{
	// procedure
}
```

`for..in` should work with:

- Object with `proxy::iterateKeys`

`for each` should work with:

- Object with `proxy::iterateValues` 
- `Iterable`
- `Iterator`
- Any type (`*`)