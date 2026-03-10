# 02. CSS Box Model and Fonts

## CSS Box Model

Every HTML element is treated as a rectangular box. The CSS Box Model consists of four layers (from inside to outside):

```
┌────────────────────────── Margin ──────────────────────────┐
│  ┌──────────────────────── Border ──────────────────────┐  │
│  │  ┌──────────────────── Padding ───────────────────┐  │  │
│  │  │  ┌──────────────── Content ─────────────────┐  │  │  │
│  │  │  │                                          │  │  │  │
│  │  │  └──────────────────────────────────────────┘  │  │  │
│  │  └────────────────────────────────────────────────┘  │  │
│  └──────────────────────────────────────────────────────┘  │
└────────────────────────────────────────────────────────────┘
```

| Layer     | Description                                      |
| --------- | ------------------------------------------------ |
| **Content** | The actual content (text, image, etc.)          |
| **Padding** | Space between content and border (transparent)  |
| **Border**  | Surrounds the padding                           |
| **Margin**  | Space outside the border (transparent)          |

---

### Universal Reset

```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
```

- Removes default browser margin & padding from all elements.
- `box-sizing: border-box` makes `width` and `height` include padding and border (not just content).

---

### Padding

Space between the **content** and the **border**.

```css
/* All four sides individually — Top Right Bottom Left (Clockwise) */
padding: 40px 20px 15px 10px;

/* Top+Bottom | Left+Right */
padding: 40px 20px;
```

| Shorthand Values        | Meaning                                |
| ----------------------- | -------------------------------------- |
| `padding: 10px`         | All sides = 10px                       |
| `padding: 10px 20px`    | Top+Bottom = 10px, Left+Right = 20px  |
| `padding: 10px 20px 15px` | Top = 10px, Left+Right = 20px, Bottom = 15px |
| `padding: 10px 20px 15px 5px` | Top, Right, Bottom, Left (clockwise) |

---

### Border

```css
border: 40px solid black;
```

- Shorthand: `width` `style` `color`
- Common styles: `solid`, `dashed`, `dotted`, `double`, `none`

---

### Margin

Space **outside** the border.

```css
margin-bottom: 100px;
margin-top: 150px;
```

#### Margin Collapse

When two vertical margins meet (e.g., `margin-bottom` of one element and `margin-top` of the next), they **collapse** — only the **larger** margin is applied, not the sum of both.

```css
.box1 { margin-bottom: 100px; }
.box2 { margin-top: 150px; }
/* Result: 150px gap between them, NOT 250px */
```

---

### box-sizing

| Value         | Behaviour                                              |
| ------------- | ------------------------------------------------------ |
| `content-box` | (Default) `width`/`height` = content only. Padding & border are added on top. |
| `border-box`  | `width`/`height` = content + padding + border. Total size stays as specified. |

---

### overflow

Controls what happens when content overflows its box.

```css
overflow: auto; /* Adds scrollbar only when needed */
```

| Value     | Behaviour                          |
| --------- | ---------------------------------- |
| `visible` | (Default) Content spills out       |
| `hidden`  | Content is clipped                 |
| `scroll`  | Always shows scrollbar             |
| `auto`    | Scrollbar only when content overflows |

---

## Inline vs Block vs Inline-Block

| Property        | Block (`div`)   | Inline (`a`, `span`) | Inline-Block        |
| --------------- | --------------- | --------------------- | ------------------- |
| Starts new line | Yes             | No                    | No                  |
| Width/Height    | Respected       | Ignored               | Respected           |
| Margin/Padding  | All sides work  | Only left/right       | All sides work      |

To make an inline element (like `<a>`) accept `width`, `height`, and vertical margin/padding:

```css
a {
    display: inline-block;
    width: 300px;
    height: 300px;
    padding: 15px 30px;
    border: 3px solid black;
    margin-right: 30px;
}
```

---

## CSS Fonts

### font-family

Sets the typeface for text. Always provide a **fallback** generic family.

```css
p {
    font-family: "Chiron Hei HK", sans-serif;
}
```

Generic font families: `serif`, `sans-serif`, `monospace`, `cursive`, `fantasy`

---

### @font-face — Using Custom / Local Fonts

You can load a font file (`.ttf`, `.woff`, `.woff2`, etc.) and give it a custom name:

```css
@font-face {
    font-family: 'MyBanglaFont';
    src: url(./fonts/Li\ Purno\ Pran\ Unicode.ttf);
}

p.bangla {
    font-family: 'MyBanglaFont', sans-serif;
}
```

**Steps:**
1. Place the font file in your project (e.g., `fonts/` folder).
2. Define `@font-face` with a custom `font-family` name and the `src` path.
3. Use that name in any selector's `font-family`.

> **Note:** The font used here is **"Li Purno Pran"** from [Lipighor](https://lipighor.com) — a free Bangla Unicode font.

---

### Font File Formats

| Format   | Extension | Browser Support         |
| -------- | --------- | ----------------------- |
| TrueType | `.ttf`    | Wide support            |
| WOFF     | `.woff`   | Modern browsers         |
| WOFF2    | `.woff2`  | Best compression, modern|
| OpenType | `.otf`    | Wide support            |

---

## Key Takeaways

- The **Box Model** is fundamental — every element has content, padding, border, and margin.
- Use `box-sizing: border-box` to make sizing predictable.
- **Margin collapse** happens only vertically between adjacent block elements.
- Use `display: inline-block` when you need inline flow **with** block-level sizing.
- Use `@font-face` to load custom/local fonts into your CSS.
