# Markup Expression

VioletScript supports markup similiar to XML, with the only exception of text nodes.

Remarks:

- The markup syntax can be used to initialize any user class with the following restrictions:
  - The class must not have a `DontInit` decorator.
  - The class constructor must be either empty or receive only optional parameters and/or rest parameter.
- A container class must implement `IMarkupContainer.<T>`.
- A curly brackets into the markup must contain an expression of the array type.

```
const c = (
	<Container>
        <Item n=Infinity v={10**2} checked/>
        {childrenArrayRest}
    </Container>
);

// qualified tag name
<com.q.a.X/>;

// qualified tag name using colon
<s:Button/>;

const a: [Container] = <>
    <Container/>
    <!-- spread -->
    { [<Container/>,<Container/>,<Container/>] }
</>;
```