---
tags:
  - "#java"
  - "#java_core"
  - fundamentals
  - primitives
---
# Character

**Related notes:** [[Primitive_Data_Types]], [[Wrapper_Class]]

---

The **char** is a **Primitive** data type used to represent a single character, such as a letter, a number, or a symbol. It uses the `char` **Keyword**, and its literals must be enclosed in **single quotes** 
(e.g., `'D'`).

---

### **Unicode Encoding**

Java uses the **Unicode** standard to encode all `char` values. This allows for the representation of international and symbolic characters.

- Each character is assigned a specific **code point** (e.g., `'D' → U+0044`).
    
- You can define characters using **Unicode escape sequences** starting with a backslash and `u`: `char ch = '\u0044'; // This represents 'D'`

---

### **Numeric Representation & Assignment**

Because characters are stored internally as numeric Unicode values, you can assign an **Integer** value directly to a `char` variable.


```
// EXAMPLE
char ch = 68;            // 'D' corresponds to Unicode code point 68
System.out.println(ch);  // Output: D
```

---

### **Arithmetic with Chars**

Since `char` values are represented by numbers, all **arithmetic operators** can be used with them. When performing arithmetic, Java uses the underlying numeric value of each character.

> **Example:** `'A' (65) + 'B' (66) = 131`