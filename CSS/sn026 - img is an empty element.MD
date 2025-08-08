This statement refers to how CSS treats `<img>` tags in the context of the `:empty` pseudo-class. It's a bit of a trick question, but the authors are correct.

Here's the breakdown:

### `<img>` Is an "Empty" HTML Element

In HTML, an `<img>` tag is what's known as a **void element** or **empty tag**. This means it **cannot have any child elements or text content between an opening and closing tag**. It's always a self-closing tag.

For example, this is valid HTML:

```html
<img src="my-image.jpg" alt="A beautiful picture">
```

But this is not:

```html
<img src="my-image.jpg" alt="A beautiful picture">This text is content</img>
```

The browser ignores any content you try to put inside an `<img>` tag. Its entire purpose and function are defined by its attributes, such as `src`, `alt`, `width`, and `height`.

-----

### The `:empty` Pseudo-Class

The `:empty` pseudo-class in CSS selects elements that have **no child elements or text content**.

Since the `<img>` tag, by its very nature, can never have any children or content, it will **always** match the `:empty` pseudo-class.

### Conclusion

Because every single `<img>` tag is always an empty element, the CSS selector `img` and the more specific selector `img:empty` will always target the exact same set of elements on a page. The two selectors are functionally identical for the `<img>` element.

[G]
