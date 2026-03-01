# 📒 MERN Stack — Study Notes

---

## 📌 Module 01: CSS (Cascading Style Sheets)

### 🗂 Files

- `index.html` — HTML document with nested `div`, `h1`, `p`, and `ul` elements used to demonstrate various CSS selectors.
- `style.css` — Stylesheet covering selectors, specificity, and combinators.

---

### 1. Universal Selector (`*`)

```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
```

| Property | What it does |
|---|---|
| `margin: 0` | Removes default outer spacing from **every** element on the page. |
| `padding: 0` | Removes default inner spacing from **every** element. |
| `box-sizing: border-box` | Makes width/height include padding & border, so elements don't overflow their declared size. |

> **Use case:** This is commonly used as a **CSS reset** to ensure consistent styling across browsers.

---

### 2. ID Selector (`#id`)

```css
#id {
    color: red;
}
```

- Targets a **single, unique** element whose `id` attribute matches.
- IDs have **high specificity** (score: `1-0-0`), so they override class and tag styles.

> **Rule:** Each `id` should appear only **once** per page.

---

### 3. Tag Selector (with ID)

```css
h1#title {
    color: red;
}
```

- Selects `<h1>` elements that **also** have `id="title"`.
- Combining a tag with an ID increases specificity, making the rule harder to override.

---

### 4. Class Selector (`.class`)

```css
li.odd {
    color: red;
}
```

- Selects all `<li>` elements that have `class="odd"`.
- Classes are **reusable** — multiple elements can share the same class.
- Specificity score: `0-1-1` (one class + one tag).

---

### 5. Attribute Selector (`[attr="value"]`)

```css
[href="https://www.google.com"] {
    color: red;
}
```

- Targets elements whose `href` attribute **exactly equals** the given URL.
- Useful for styling specific links, inputs, or any element with a particular attribute value.

---

### 6. Specificity

Specificity determines **which rule wins** when multiple rules target the same element.

| Selector | Specificity Score | Priority |
|---|---|---|
| `*` (universal) | `0-0-0` | Lowest |
| `h1` (tag) | `0-0-1` | Low |
| `.class` | `0-1-0` | Medium |
| `#id` | `1-0-0` | High |
| `!important` | — | **Overrides everything** |

#### Example — ID vs Tag:

```css
#title {
    color: red;    /* ← Wins (specificity 1-0-0) */
}
h1 {
    color: blue;   /* ← Loses (specificity 0-0-1) */
}
```

#### Example — `!important` overrides all:

```css
li {
    color: blue;
}
* {
    color: red !important;  /* ← Wins on every element, even over li */
}
```

> ⚠️ **Avoid `!important`** in production code — it makes debugging very difficult.

---

### 7. CSS Combinators

Combinators define the **relationship** between selectors.

---

#### 7a. Descendant Combinator (` ` space)

```css
div.first-div h1 {
    color: red;
}
```

- Selects **all** `<h1>` elements that are **anywhere inside** `div.first-div`, no matter how deeply nested.
- In the HTML, this would target:
  - `<h1>Hello World 1</h1>`
  - `<h1>Hello Inner World</h1>` (inside `.inner-div`)
  - `<h1>Hello World 2</h1>`

---

#### 7b. Child Combinator (`>`)

```css
.first-div > h1 {
    color: red;
}
```

- Selects `<h1>` elements that are **direct children** of `.first-div` only.
- **Does NOT** select `<h1>Hello Inner World</h1>` because it's inside `.inner-div` (not a direct child).
- Targets:
  - `<h1>Hello World 1</h1>` ✅
  - `<h1>Hello World 2</h1>` ✅
  - `<h1>Hello Inner World</h1>` ❌

---

#### 7c. Next Sibling Combinator (`+`)

```css
h1 + p {
    color: red;
}
```

- Selects a `<p>` that is the **immediately next sibling** after an `<h1>`.
- Only the **first** `<p>` right after `<h1>` is selected — not subsequent `<p>` tags.

---

#### 7d. Subsequent-Sibling Combinator (`~`)

```css
h1 ~ p {
    color: red;
}
```

- Selects **all** `<p>` siblings that come **after** an `<h1>`, not just the immediate next one.
- Both the long paragraph and `<p>Second P</p>` would be selected.

---

#### 7e. Combined Combinator (Active Rule)

```css
body > .first-div > h1 + p {
    color: red;
}
```

This is the **currently active** (uncommented) rule. Breaking it down step by step:

| Step | Selector | Meaning |
|---|---|---|
| 1 | `body >` | Start from `<body>`, select direct children only |
| 2 | `.first-div >` | Then narrow to direct children of `.first-div` |
| 3 | `h1 + p` | Then select a `<p>` that **immediately follows** an `<h1>` |

**Result:** Only the long `<p>Lorem ipsum...</p>` paragraph turns **red**, because it is the first `<p>` directly after `<h1>Hello World 2</h1>` inside `.first-div`.

---

---

## 📌 Module 03: JavaScript — Introduction

### 🗂 File

- `app.js` — Covers variables, data types, `typeof` operator, type coercion, and increment/decrement operators.

---

### 1. Variable Declaration — `var` vs `let`

```js
var x = 10;
var x = 20;   // Allowed — var can be re-declared
console.log(x); // 20
```

- `var` allows **re-declaration** of the same variable — the latest value wins.
- `let` does **not** allow re-declaration in the same scope (throws an error).

---

### 2. Data Types & `typeof`

| Type | Example | `typeof` returns |
|---|---|---|
| **Number** | `let num = -10;` | `"number"` |
| **String** | `let fullName = 'Ishan Khan';` | `"string"` |
| **Float** | `let num = -10.5;` | `"number"` (no separate float type) |
| **Boolean** | `let isProgrammer = false;` | `"boolean"` |
| **Undefined** | `let und = undefined;` | `"undefined"` |
| **Null** | `let none = null;` | `"object"` ⚠️ (known JS bug) |
| **Array** | `let arr = [1,2,3];` | `"object"` |
| **Object** | `let arr = {a: 1};` | `"object"` |

> ⚠️ `typeof null` returns `"object"` — this is a [legacy bug](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof#typeof_null) in JavaScript that was never fixed.

---

### 3. Double `typeof`

```js
let num = -10.5;
console.log(typeof typeof(num)); // "string"
```

- `typeof(num)` → `"number"` (a string)
- `typeof "number"` → `"string"`

> **Trick question:** `typeof` always returns a **string**, so `typeof typeof(anything)` is always `"string"`.

---

### 4. String Methods

```js
let str = "Hello, World!";
console.log(str.toUpperCase()); // "HELLO, WORLD!"
```

- `.toUpperCase()` converts all characters to uppercase.
- Strings are **immutable** — the original `str` is not changed.

---

### 5. Type Coercion (Implicit Conversion)

```js
let num1 = '10';
let num2 = '10';
console.log(num1 - num2); // 0
```

- The `-` operator **coerces** strings to numbers automatically.
- `'10' - '10'` becomes `10 - 10` = `0`.
- ⚠️ The `+` operator would **concatenate** instead: `'10' + '10'` = `"1010"`.

---

### 6. Pre-Decrement Operator (`--num`)

```js
let num = 10;
let newNum = --num;
console.log(newNum); // 9
```

| Operator | Name | Behavior |
|---|---|---|
| `--num` | **Pre-decrement** | Decrements first, then assigns → `newNum = 9` |
| `num--` | **Post-decrement** | Assigns first, then decrements → `newNum = 10`, but `num` becomes `9` |
| `++num` | **Pre-increment** | Increments first, then assigns |
| `num++` | **Post-increment** | Assigns first, then increments |

---

## 📝 Quick Reference — CSS Selector Cheat Sheet

```
*              → All elements
#id            → Element with specific id
.class         → Elements with specific class
tag            → All elements of that tag
tag.class      → Tag with specific class
tag#id         → Tag with specific id
[attr="val"]   → Elements with exact attribute value
A B            → B anywhere inside A (descendant)
A > B          → B direct child of A
A + B          → B immediately after A (next sibling)
A ~ B          → All B after A (subsequent siblings)
```

---

*Notes generated from the MERN Stack learning repository by Ishan Khan.*
