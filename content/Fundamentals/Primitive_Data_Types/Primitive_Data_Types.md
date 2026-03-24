---
tags:
  - java
  - java_core
  - "#fundamentals"
  - "#primitives"
---
# Primitive Data Types

**Related notes:** [[Integer_Types]], [[Floating-Point_Types]], [[Character]], [[Boolean]], [[Wrapper_Class]], [[Casting]]

---

**Primitive Data Types** are the fundamental building blocks of Java used for storing simple values such as numbers, characters, or logical states. Unlike reference types, primitives are **not Objects**; they are defined using Java **Keywords** and store their values directly in memory rather than as references.

Primitives are a core part of the broader concept of **Data Types** (or Classes).

---

### **List of Basic Data Types**

Java provides eight primitives, categorized into four groups:

- **Integers:** `byte`, `short`, `int`, `long` (for whole numbers).
    
- **Floating-point:** `float`, `double` (for decimal numbers).
    
- **Character:** `char` (for single characters/Unicode).
    
- **Boolean:** `boolean` (for `true`/`false` states).


> **Note:** If you need to treat these primitives as objects (for example, to store them in a Collection), you can use their corresponding **Wrapper Class** (e.g., `Integer` for `int`).

---

### **Casting and Data Integrity**

To avoid data loss or runtime errors when performing operations between different primitive types, you must use **type Casting**. This is especially important when moving from a larger type (like `double`) to a smaller type (like `int`).

---

### **Limits: Overflow and Underflow**

**Overflow** and **Underflow** occur when a calculation produces a value that exceeds the defined limits (`MIN_VALUE` or `MAX_VALUE`) of its data type.

- **Overflow:** Occurs when a value becomes greater than the `MAX_VALUE`.
    
- **Underflow:** Occurs when a value becomes smaller than the `MIN_VALUE`.

**Behavior:** Exceeding these limits leads to unexpected behavior, such as "wrapping around" to the opposite extreme value.

```
// EXAMPLE
byte b = 127; // Max value for byte
b++;          // b becomes -128 (overflow/wrap around)
```

>**Compiler Guardrail:** If you attempt to **hardcode** an out-of-range value directly (e.g., `byte b = 200;`), the compiler will detect this and throw an error immediately.