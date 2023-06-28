# Proxies

VioletScript supports proxies to alter the behavior of certain operations. Currently, only `class` and `enum` can define proxies; `interface` cannot define proxies.

Proxies cannot be overriden by subclasses.

## Conversion Proxies

These proxies do not enable use of the literal `this`.

```
class C {
    proxy function convertImplicit(a: T): C? {
        // implicit conversion from A to C
    }

    proxy function convertExplicit(a: T): C? {
        // explicit conversion from A to C
    }
}
```

## Unary Operator Proxies

These proxies do not enable use of the literal `this`.

```
class C {
    // +o;
    proxy function positive(a: C): R ...;

    // -o;
    proxy function negate(a: C): R ...;

    // ~o;
    proxy function bitNot(a: C): R ...;
}
```

## Binary Operator Proxies

These proxies do not enable use of the literal `this`.

```
class C {
    // a === b;
    proxy function equals(a: C, b: C): Boolean ...;

    // a !== b;
    proxy function notEquals(a: C, b: C): Boolean ...;

    // a < b;
    proxy function lt(a: C, b: C): Boolean ...;

    // a > b;
    proxy function gt(a: C, b: C): Boolean ...;

    // a <= b;
    proxy function le(a: C, b: C): Boolean ...;

    // a >= b;
    proxy function ge(a: C, b: C): Boolean ...;

    // a + b;
    proxy function add(a: C, b: B): R ...;

    // a - b;
    proxy function subtract(a: C, b: B): R ...;

    // a * b;
    proxy function multiply(a: C, b: B): R ...;

    // a / b;
    proxy function divide(a: C, b: B): R ...;

    // a % b;
    proxy function remainder(a: C, b: B): R ...;

    // a ** b;
    proxy function pow(a: C, b: B): R ...;

    // a & b;
    proxy function bitAnd(a: C, b: B): R ...;

    // a ^ b;
    proxy function bitXor(a: C, b: B): R ...;

    // a | b;
    proxy function bitOr(a: C, b: B): R ...;

    // a << b;
    proxy function leftShift(a: C, b: B): R ...;

    // a >> b;
    proxy function rightShift(a: C, b: B): R ...;

    // a >>> b;
    proxy function unsignedRightShift(a: C, b: B): R ...;
}
```

## Index Proxies

These proxies enable use of the literal `this`.

```
class C {
    // o[i];
    proxy function getIndex(i: I): V (
        ...
    );

    // o[i] = v;
    proxy function setIndex(i: I, v: V): void {
        ...
    }

    // delete o[i];
    proxy function deleteIndex(i: I): Boolean {
    	...
    }

    // v in o;
    proxy function has(v: V): Boolean (
    	...
    );
}
```

## Iteration Proxies

These proxies enable use of the literal `this`.

```
class C {
    // for..in
    proxy function iterateKeys(): Generator.<K> {
        // yield
    }

    // for each
    proxy function iterateValues(): Generator.<V> {
        // yield
    }
}
```