# Binary Expression

```
k in o;
x + y
x - y
x * y
x / y
x % y // remainder
x ** y
x && y
x ^^ y
x || y
x ?? y
x & y
x ^ y
x | y
x << y
x >> y
x >>> y
x == y
x != y
x === y
x !== y
x < y
x > y
x <= y
x >= y
nonDestructuringPattern = y
destructuringPattern = y
nonDestructuringPattern compound= y

v is T;
v is q : Q;
v instanceof T;

// optional conversion; both equivalent
v as T;
v as? T;

// forced conversion
v as! T;
```

## Assignment

- Assignment is only allowed as a statement, as a `for` update and as the right-hand side of another assignment.
- It is allowed to use compound assigning applied to non-null index:
```
o[k]! += 1;
```