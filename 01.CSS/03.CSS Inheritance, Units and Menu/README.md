# 03. CSS Inheritance, Units and Menu

This section covers practical UI styling with lists/menus and introduces common CSS measurement units.

## What You Learn

- CSS inheritance basics and how default styles cascade to child elements.
- Common absolute and relative CSS units.
- Building a horizontal navigation menu with `<ul>`, `<li>`, and `<a>`.
- Interactive menu hover effects using transition, border radius, and box shadow.
- Creating custom shapes with `clip-path`.

---

## Files in This Topic

| File | Purpose |
| ---- | ------- |
| `list.html` | Demonstrates list styling, horizontal nav menu, hover effects, and a `clip-path` shape |
| `units.html` | Demonstrates absolute vs relative units and a full viewport section using `vw`/`vh` |
| `notes.md` | Quick summary notes for this topic |

---

## Key Concepts

### 1. CSS Inheritance

Some properties are inherited by child elements (for example, `color`, `font-family`), while layout properties like `margin`, `padding`, and `border` are generally not inherited.

Why this matters:
- It reduces repeated CSS when setting shared text styles at parent level.
- It helps you predict when child elements need explicit overrides.

### 2. CSS Units

Absolute units:
- `px`, `cm`, `mm`, `in`, `pt`, `pc`

Relative units:
- `em`, `rem`, `vw`, `vh`, `vmin`, `vmax`, `%`

Quick notes:
- `1em` depends on the parent element's font size.
- `1rem` depends on the root (`html`) font size.
- `100vw` and `100vh` are useful for full-screen sections.

### 3. Menu Styling from `list.html`

Main techniques used:
- Remove default list spacing with:

```css
ul {
    margin: 0;
    padding: 0;
    list-style: none;
}
```

- Place menu items in one row with:

```css
ul li {
    display: inline-block;
}
```

- Style links as button-like items with padding, background, and hover transitions.

### 4. Shape with `clip-path`

`clip-path` is used to visually cut an element into a custom polygon.

Example from this topic:

```css
div {
    clip-path: polygon(0% 20%, 60% 20%, 60% 0%, 100% 50%, 60% 100%, 60% 80%, 0% 80%);
}
```

---

## Practice Ideas

1. Convert the menu to use Flexbox instead of `inline-block`.
2. Add an active menu state (for example, `Home` highlighted).
3. Build a hero section with `height: 100vh` and centered content.
4. Replace `tomato` with a custom color palette.

---

## Summary

By the end of this topic, you can style list-based navigation menus, apply hover interactions, and choose the right CSS units for responsive layouts.