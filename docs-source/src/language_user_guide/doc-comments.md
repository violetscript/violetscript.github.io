# Documentation Comments

VioletScript supports Markdown comments with special `@` tags. They're called VioletDoc comments.

Here is an example:

```
/**
 * The function `f` does nothing.
 *
 * @example
 *
 * ```
 * f();
 * ```
 *
 * @throws {ArgumentError} If argument is invalid.
 */
function f(): void {
}
```

## Supported Tags

- `@deprecated`
- `@param paramName Description.`
- `@return A return value.`
- `@throws {C} Optional description.`
- `@internal Internal comment.`

## Structural Types

VioletDoc comments on individual record fields are not supported currently:

```
type R = {
    /**
     * Some field.
     */
    someField: String,
};
```

You can attach a VioletDoc comment to the type alias in this situation.