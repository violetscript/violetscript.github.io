# Classes

```
class C {
	// constructor
	function C() {
		super();
	}

	// override instance method
	override function toString(): String (
		'violetscript'
	);

	// final instance method: cannot be overriden
	// by subtypes.
	final function finalMethod(): void {
	}
}

class F extends C implements I {
}

// generic class
class G.<T> {
}

// final class: cannot extend
final class Final {
}
```

## Prohibit Object Initialiser

Use the `DontInit` decorator to prohibit object initializer on a specific class.

```
[DontInit]
class C {
}

var o: C = {}; // VerifyError!
```

# Method Overriding

- An override can specify either additional optional parameters or one additional rest parameter.
- An override can specify a more specific return type: either a subtype or, if the original method's return is `*`, any different type.