---
tags:
  - "#java"
  - "#java_core"
  - fundamentals
  - primitives
---
# Floating-Point Type

**Related notes:** [[Primitive_Data_Types]], [[Wrapper_Class]]

---

The floating-point types are **Primitives** used to define **Variables** that store decimal numbers (numbers with fractional parts). In Java, `double` is the **default type** for any decimal literal.

---
### **Types of Decimal Numbers**

Java provides two primitive types for decimal numbers, which differ in their precision and the range of values they can store:

|**Type**|**Size (bits)**|**Keyword**|
|---|---|---|
|**`float`**|32-bit|`float`|
|**`double`**|64-bit|`double`|

---

### **Assignment Rules & Suffixes**

Because the compiler treats all decimal literals as `double` by default, specific suffixes must be used during assignment:

- **Float Suffix (`F`):** If you want to assign a value to a `float` variable, you **must** use the suffix `F` (or `f`). Without it, the compiler treats the number as a `double` and throws an error.
    
    - _Example:_ `float var = 1.45F;`
        
- **Double Suffix (`D`):** You can use the suffix `D` (or `d`) for double numbers, but it is **optional**. Its primary purpose is to improve clarity for the reader.
    
    - _Example:_ `double var = 1.45;` or `double var = 1.45D;`