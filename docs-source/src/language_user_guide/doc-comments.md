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
- `@hidden`
- `@example Example section.`
- `@param paramName Description.`
- `@return A return value.`
- `@throws {C} Optional description.`
- `@internal Internal comment.`
- `@field {x} Field commment`
  - Used internally when you add comment to a record field in a type alias to a record type.
  - It allows dot too for documenting subfields.