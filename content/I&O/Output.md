---
tags:
  - "#java"
  - "#java_core"
  - I/O
  - output
---
# Output

**Related notes:** [[Class]], [[Input]], [[Formatting]]

---

In Java, output is handled primarily through two standard streams: **`System.out`** (for standard output) and **`System.err`** (for error messages). Both are instances of the `PrintStream` class, providing a set of flexible methods to display data to the user.

---

### 1. `System.out` (Standard Output)

This is the primary way to communicate with the user. Whether you are printing plain text or formatted data, `System.out` provides several specialized methods:

- **`print()`**: Outputs data as a string and keeps the cursor on the **same line**.
    
- **`println()`**: Short for "print line." It outputs the data and then automatically moves the cursor to the **next line**.
    
- **`printf()` / `format()`**: Used for **Formatted Output**. This allows you to insert variables into a template string using placeholders.
    
- **`append(char c)`**: A lower-level method that adds a single character to the stream.
    
- **`write(byte[] b)`**: Used for writing raw bytes directly, useful when dealing with binary data rather than text.

---

### 2. Escape Sequences

Since certain characters (like quotes or new lines) have special meanings in Java code, you must use a backslash (`\`) to "escape" them so they print literally.

|**Sequence**|**Description**|**Result**|
|---|---|---|
|**`\n`**|**New Line**|Cursor moves to the start of the next line.|
|**`\t`**|**Tab**|Inserts a horizontal tab space.|
|**`\"`**|**Double Quote**|Allows you to print a `"` inside a string literal.|
|**`\\`**|**Backslash**|Allows you to print a literal `\` character.|

---

### 3. `System.err` (Standard Error)

**`System.err`** is designed specifically for error messages, warnings, and diagnostic information.

- **Visual Distinction:** In many IDEs (like IntelliJ or Eclipse), `System.err` text is automatically colored **red** to grab the developer's attention.
    
- **Stream Separation:** While both usually show up in the same console, they are technically different streams. You can redirect `System.out` to a text file while still letting `System.err` show up on your screen.

```
try {
    int result = 10 / 0;
} catch (ArithmeticException e) {
    System.err.println("CRITICAL ERROR: Division by zero!");
}
```
