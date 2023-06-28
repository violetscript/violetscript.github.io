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

- Generator functions return a Generator iterator.
- A generator function finishes returning undefined.

```
function f(): Generator.<Number> {
	yield 10;
}

const it = f(); // Iterator.<Number>
it.next(); // {done: false, value: 10}
it.next(); // {done: true, value: undefined}
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