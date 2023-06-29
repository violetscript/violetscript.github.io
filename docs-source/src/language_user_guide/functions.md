# Functions

```
function f(): void {
}

function fWithRequiredParameter(a: Number): void {
}

function fWithOptionalParameter(a: Number = 10): void {
}

function fWithRestParameter(...a: [Number]): void {
}

function fWithExpressionBody(): String (
	'violetscript'
);

// native function
native function fNative(): void;
```

## Generators

A function is a generator if it uses the `yield` operator.

Remarks:

- Generator functions return a Generator object, which is an iterator.
- A generator function finishes returning `undefined`.

```
function f(): Iterator.<Number> {
	yield 10;
}

const iterator = f(); // Iterator.<Number>
iterator .next(); // {done: false, value: 10}
iterator .next(); // {done: true, value: undefined}
```

## Asynchronous Functions

A function is asynchronous if it uses the `await` operator.

Remarks:

- Asynchronous functions return Promise.
- Any thrown errors will reject the Promise.

```
function f(): Number {
	await a();
	return 10;
}
```

## Generic Functions

```
function genericFunction.<T>(): void {
}
```