# Meta-data

Compile-time meta-data can be attached to any definition through the `[Metadata()]` decorator. It can contain any kind of data.

Any added meta-data is erased at runtime.

```
package q {
    [Metadata(x = '')]
    public function f(): void {
    }
}
```