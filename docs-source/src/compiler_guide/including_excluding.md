# Including and Excluding Sources

The compiler does not accept globbing patterns or specifying a directory for including sources recursively. This is so that you specify sources in the correct order for static property initialization.

Generally you must have an entry script including other scripts:

```
include './script1';
include './script2';
```