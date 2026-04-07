# Module 04: CSS Backgrounds and Links

This folder contains practice files for CSS background properties and anchor/button styling.

## Files

| File | Purpose |
|---|---|
| `background.html` | Practice with `background-image`, gradients, repeat, size, and position |
| `button.html` | Practice styling links like buttons with hover effects |
| `notes.md` | Written notes for this module |

## Topics Covered

- Background images
- Linear gradients
- Multiple backgrounds
- `background-repeat`
- `background-size`
- `background-position`
- Styling `<a>` tags as buttons
- Hover transitions
- Full-width button styles

## Quick Examples

### Background

```css
.box {
  background-image: linear-gradient(to left, red, blue);
  background-repeat: no-repeat;
  background-size: 500px;
  background-position: top center;
}
```

### Button

```css
.btn {
  display: inline-block;
  background-color: #0a5ed7;
  padding: 15px 20px;
  color: #fff;
  border-radius: 10px;
  text-decoration: none;
  transition: all 0.3s;
}

.btn:hover {
  color: #0a5ed7;
  background-color: transparent;
}
```

## Goal

Understand how CSS can control page backgrounds and turn simple links into reusable button components.
