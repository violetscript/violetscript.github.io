# Strictness

## Shadowing variables

The `"use shadowing"` pragma allows shadowing all variables in a scope:

```
{
    'use shadowing'
    var x = ''
    var x = 0
}
```