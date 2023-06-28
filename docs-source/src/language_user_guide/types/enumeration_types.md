# Enumeration Types

Enumeration types define variants with an unique number and an unique string.

The following example program defines an enumeration with four variants:

```
enum E {
	VARIANT_A;
	VARIANT_B = 'customizedName';
	VARIANT_C = 64;
	VARIANT_D = ['anotherCustomizedName', 10];
}

// inference: 'variantA' converts to E.VARIANT_A
var e: E = 'variantA';

E.VARIANT_A.valueOf() == 0;
E.VARIANT_A.toString() == 'variantA';

E.VARIANT_B.valueOf() == 1;
E.VARIANT_B.toString() == 'customizedName';

E.VARIANT_C.valueOf() == 64;
E.VARIANT_C.toString() == 'variantC';

E.VARIANT_D.valueOf() == 10;
E.VARIANT_D.toString() == 'anotherCustomizedName';
```

## Custom Properties

The block of an `enum` definition can contain anything, as the following program demonstrates:

```
enum E {
	function f(): void {
	}
}
```

## Type Inference

Wherever a value of an `enum` is expected, a string literal can be used. In addition, for flags enumerations, an object initializer, array initializer or `undefined` can also be used.

```
var e: E = E.VARIANT_A
var e: E = 'variantA'

// flags inference
var f: F = undefined
var f: F = {}
var f: F = []
```

## Flags

Flags enumerations, prefixed with the special `Flags` decorator, define combinatory variants. A variant number is either 1 or power of two.

```
[Flags]
enum F {
	A; // 1
	B; // 2
	C; // 4
}

var f: F = [ 'a' ];
var q: F = { b: true };

f += 'c'; // f.include('c')
f -= 'c'; // f.exclude('c')
f = f.toggle('c');
f = f.filter('c');
'c' in f;

// returns F value with all flags present
F.all;

// checks if flags are empty
f == []
f == undefined
```

## Custom Numeric Type

Use the context word `wraps` to use a custom numeric type for an enumeration.

```
enum E wraps BigInt {
}
```