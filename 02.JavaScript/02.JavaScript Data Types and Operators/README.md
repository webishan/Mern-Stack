# JavaScript Data Types and Operators

This topic explains the core JavaScript data types, type conversion rules, and operators you will use in almost every program.

## Learning Goals

By the end of this topic, you should be able to:
- Identify primitive and non-primitive data types in JavaScript.
- Use `typeof` and understand common edge cases.
- Convert values safely between string, number, and boolean.
- Apply arithmetic, comparison, logical, and assignment operators correctly.
- Predict expression results using operator precedence.

## 1) JavaScript Data Types

JavaScript has two broad categories of data types.

### Primitive Types

Primitive values are immutable and stored by value.

| Type | Example | Notes |
|---|---|---|
| `string` | `"hello"` | Text data inside single, double, or backtick quotes |
| `number` | `42`, `3.14`, `NaN` | JavaScript uses one numeric type for integers and floats |
| `bigint` | `123n` | For very large integers beyond `Number.MAX_SAFE_INTEGER` |
| `boolean` | `true`, `false` | Logical true/false values |
| `undefined` | `let x;` | Variable declared but not assigned |
| `null` | `let x = null;` | Intentional empty value |
| `symbol` | `Symbol("id")` | Unique identifiers, often used in objects |

### Non-Primitive Type

| Type | Example | Notes |
|---|---|---|
| `object` | `{}`, `[]`, `new Date()` | Reference type; arrays and functions are object-based |

Important `typeof` results:
- `typeof "abc"` -> `"string"`
- `typeof 10` -> `"number"`
- `typeof true` -> `"boolean"`
- `typeof undefined` -> `"undefined"`
- `typeof null` -> `"object"` (historical JavaScript behavior)
- `typeof []` -> `"object"`
- `typeof function () {}` -> `"function"`

## 2) Type Conversion (Coercion and Explicit Conversion)

### Explicit Conversion

- `Number("25")` -> `25`
- `String(25)` -> `"25"`
- `Boolean(1)` -> `true`

### Implicit Conversion (Coercion)

JavaScript may convert values automatically in expressions.

- `"5" + 1` -> `"51"` (number converted to string)
- `"5" - 1` -> `4` (string converted to number)
- `true + 1` -> `2` (`true` becomes `1`)
- `false + 1` -> `1` (`false` becomes `0`)

Common falsy values:
- `false`
- `0`
- `""`
- `null`
- `undefined`
- `NaN`

Everything else is truthy.

## 3) Operators in JavaScript

### Arithmetic Operators

- `+` addition
- `-` subtraction
- `*` multiplication
- `/` division
- `%` remainder
- `**` exponentiation

### Assignment Operators

- `=` assign
- `+=`, `-=`, `*=`, `/=`, `%=` compound assignment

### Comparison Operators

- `==` loose equality (allows type coercion)
- `===` strict equality (no type coercion)
- `!=`, `!==`
- `>`, `<`, `>=`, `<=`

Best practice:
- Prefer `===` and `!==` to avoid unexpected coercion bugs.

### Logical Operators

- `&&` AND
- `||` OR
- `!` NOT

Short-circuit behavior:
- `a && b` returns first falsy value or last value.
- `a || b` returns first truthy value or last value.

### Increment and Decrement

- `x++` post-increment
- `++x` pre-increment
- `x--` post-decrement
- `--x` pre-decrement

Difference:
- Post form returns old value first, then updates.
- Pre form updates first, then returns new value.

## 4) Operator Precedence

Expressions are evaluated based on precedence.

Example:
- `2 + 3 * 4` -> `14`

Use parentheses to make intent clear:
- `(2 + 3) * 4` -> `20`

## 5) Quick Practice

Try these in `datatype.js`:

```js
console.log(typeof null);
console.log("5" + 2);
console.log("5" - 2);
console.log(2 + 3 * 4);
console.log((2 + 3) * 4);
console.log(Boolean(""));
console.log(Boolean("hello"));
```

Expected learning outcome:
- You should be able to explain each output and the rule behind it.

## 6) Common Mistakes to Avoid

- Using `==` when you actually need `===`.
- Assuming `null` and `undefined` are the same in all cases.
- Forgetting that `+` can concatenate strings.
- Relying on implicit coercion in complex conditions.

## Next Step

After mastering this topic, continue with arrays, objects, and functions to build real program logic.
