---
tags:
  - "#java"
  - "#java_core"
  - text
---
# Formatting

**Related notes:** [[String]]

---

## Format Specifiers in Java

In Java, **Format Specifiers** are placeholders within a format string that define how data should be displayed. They act as instructions for the `printf()`, `String.format()`, and `.formatted()` methods, allowing you to control alignment, precision, and symbols with surgical precision.

---

### The Anatomy of a Specifier

The full syntax of a format specifier is:

`% [argument_index$] [flags] [width] [.precision] type`

#### 1. Type (The Mandatory Part)

This tells Java what data type it is looking at.

- **`%d`**: Integer (decimal).
    
- **`%f`**: Floating-point.
    
- **`%s`**: String.
    
- **`%b`**: Boolean.
    
- **`%n`**: Platform-independent newline (preferred over `\n`).

#### 2. Width and Alignment

**Width** sets the minimum number of characters. If the value is shorter, Java fills the rest with spaces.

- `%10s`: Right-aligns the string within a 10-character block.
    
- `%-10s`: **Left-aligns** the string within a 10-character block (using the `-` flag).

#### 3. Precision

Used primarily for numbers to define decimal places, or for strings to truncate length.

- `%.2f`: Rounds a float/double to **two decimal places**.
    
- `%.5s`: Prints only the **first five characters** of a string.

#### 4. Flags

Flags modify the visual style of the output:

- **`,`**: Adds a locale-specific thousands separator (e.g., `1,000,000`).
    
- **`0`**: Pads numbers with leading zeros instead of spaces (e.g., `00042`).
    
- **`+`**, `-`: Forces the inclusion of a sign (+ or -) for numerical values.
    
- **`(`**: Wraps negative numbers in parentheses instead of using a minus sign.
    
- **`#`**: Add prefix for numbers (hex, oct) `%#x → 0x1a`

---

### Argument Indexing

Indexing allows you to reuse the same arguments multiple times or change the order in which they appear in the final string.

```
// %2$ refers to the 2nd argument, %1$ refers to the 1st
System.out.printf("%2$s is %1$d years old. Again, %2$s is %1$d.", 30, "Alice");
// Output: Alice is 30 years old. Again, Alice is 30.
```

---

### Formatting Methods Summary

Java provides three primary ways to generate these formatted strings, depending on whether you want to print them immediately or store them for later.

|**Method**|**Usage**|**Best For**|
|---|---|---|
|**`System.out.printf()`**|`printf(format, args)`|Immediate console output.|
|**`String.format()`**|`String.format(format, args)`|Storing a formatted string in a variable.|
|**`.formatted()`**|`"template".formatted(args)`|Modern (Java 15+), fluent syntax for quick formatting.|

```
// Example of the modern .formatted() approach
String report = "| %-10s | %03d | %.2f |%n"
                .formatted("Item A", 5, 12.998);
System.out.print(report); 
// Output: | Item A     | 005 | 13.00 |
```

> **Peer Tip:** When building large tables or logs in the console, `printf` is your best friend. It ensures that columns line up perfectly regardless of whether the text inside is 3 characters or 20 characters long.

---

All about formatting [here](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Formatter.html)