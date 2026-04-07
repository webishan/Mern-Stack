# Module 01: CSS (Cascading Style Sheets)

## 04. CSS Backgrounds and Links

This section covers how to style element backgrounds and link/button-like anchors using core CSS properties.

## Topics Covered

| # | Topic | Description |
|---|---|---|
| 01 | Backgrounds | `background-image`, `background-repeat`, `background-size`, `background-position`, gradients |
| 02 | Links as Buttons | Styling `<a>` tags with padding, colors, border radius, and hover transitions |
| 03 | Utility Styles | Reusable classes like full-width (`.block`) and fixed-width (`.xl`) buttons |

## Background Notes

### Useful Properties

- `background-image`: Adds one or multiple backgrounds (images, gradients).
- `background-repeat`: Controls tiling (`repeat`, `no-repeat`, etc.).
- `background-size`: Sets image size (`cover`, `contain`, fixed values).
- `background-position`: Sets where the background appears.

### Example

```css
.box {
  width: 1200px;
  height: 1000px;
  border: 5px solid black;
  margin: 0 auto;

  /* Current file uses a linear gradient */
  background-image: linear-gradient(to left, red, blue);
  background-repeat: no-repeat;
  background-size: 500px;
  background-position: top center;
}
```

## Link/Button Notes

### Why use `<a>` as a button?

When the action is navigation, an anchor (`<a>`) is semantically correct and can be styled like a button.

### Common Button Styles

- `display: inline-block` to apply width/padding properly.
- `text-decoration: none` to remove underline.
- `border` + `border-radius` for shape.
- `transition` for smooth hover effect.

### Example

```css
.btn {
  display: inline-block;
  background-color: #0a5ed7;
  padding: 15px 20px;
  color: #fff;
  border-radius: 10px;
  text-decoration: none;
  transition: all 0.3s;
  border: 1px solid #0a5ed7;
}

.btn:hover {
  color: #0a5ed7;
  background-color: transparent;
}

.block {
  width: 100%;
  text-align: center;
}
```

## Practice Ideas

- Add a second background layer (image + gradient).
- Try `background-size: cover` on a hero section.
- Create variants like `.btn-secondary` and `.btn-outline`.

## Files In This Folder

- `background.html`
- `button.html`
- `notes.md`
