---
tags:
  - "#java"
  - "#java_core"
  - text
---
# Text_Block

**Related notes:** [[String]], [[Formatting]]

---

A **Text Block** is a multi-line string literal that allows you to write formatted, multi-line text without the "clutter" of concatenation (`+`) or explicit escape sequences like `\n`. Introduced as a standard feature in **Java 15**, it is particularly powerful for handling structured data like HTML, JSON, or SQL queries directly within your code.

---

### The Syntax

A text block starts and ends with **triple double quotes** (`"""`).

- **Opening:** The opening `"""` must be followed by a **new line**. You cannot put content on the same line as the opening quotes.
    
- **Closing:** The closing `"""` can be on its own line or at the end of the last line of text. Its position determines how trailing whitespace and the final new line are handled.

```
String sql = """
             SELECT id, name, email
             FROM users
             WHERE status = 'ACTIVE'
             ORDER BY name;
             """;
```

---

### Key Characteristics

#### 1. Incidental Whitespace (Automatic Trimming)

Java automatically determines the "base" indentation of the text block. It looks for the leftmost character in the entire block and treats everything to the left of that as **incidental whitespace**, which is then removed. This allows you to keep your text block aligned with your code without those leading spaces showing up in the actual string.

#### 2. Escape Sequences

In a text block, you generally **do not need to escape** double quotes (`"`). You only need to escape triple double quotes if they are part of your text.

- **`\` (Line Joiner):** Use a backslash at the end of a line to tell Java _not_ to insert a new line character there. This is great for keeping long strings readable in code while keeping them on one line at runtime.
    
- **`\s` (Space Preserver):** Use this to ensure trailing spaces are not stripped away by the compiler.

#### 3. Preserved Formatting

The formatting you see in your IDE is exactly what the string will contain at runtime (minus the incidental indentation). This makes debugging HTML or JSON templates significantly easier.

---

### Comparison: Traditional vs. Text Block

|**Feature**|**Traditional String ("...")**|**Text Block ("""...""")**|
|---|---|---|
|**Multi-line**|Requires `+` and `\n`|Natural line breaks|
|**Quotes**|Requires `\"`|Plain `"` is allowed|
|**Readability**|Low (cluttered with syntax)|High (looks like the raw data)|
|**SQL/JSON**|Difficult to copy-paste|Copy-paste friendly|

```
// The "Hard" Way
String jsonOld = "{\n" +
                 "  \"name\": \"Alice\",\n" +
                 "  \"age\": 30\n" +
                 "}";

// The "Text Block" Way
String jsonNew = """
                 {
                   "name": "Alice",
                   "age": 30
                 }
                 """;
```

> **Peer Tip:** Text blocks are a "developer-friendly" feature. While they look different in your `.java` file, at runtime, they are just regular `String` objects. You can use all the standard methods like `.trim()`, `.substring()`, or `.formatted()` on them just as you would with any other string.