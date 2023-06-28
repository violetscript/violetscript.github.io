# Import Directive

```
import q.u.*;
import q.**; // recursive; imports `q` and all subpackages
import q.u.B;
import A = q.u.B;
import Qu = q.u.*;
```

## Import from global

The `global` identifier may be used to alias a property of the global package.

```
import GRegExp = global.RegExp;
```

## Subpackage aliasing

A subpackage from a package can be accessed even when the base package is aliased.

```
// com.scientific.fns.f
import sci = com.scientific.*;
sci.fns.f();
```