---
tags:
  - "#java"
  - "#java_core"
  - fundamentals
  - primitives
---
# Integer Types

**Related notes:** [[Primitive_Data_Types]], [[Wrapper_Class]]

---

An **Int** is a **Primitive** data type used to define **Variables** that store whole numbers. In Java, `int` is considered the **default type** for integer literals.

---

### **The Four Integer Types**

Java provides four distinct integer types that differ based on their memory usage (bit size) and the range of numbers they can hold:

|**Keyword**|**Size (Bits)**|**Description**|
|---|---|---|
|**`byte`**|8-bit|Smallest integer type.|
|**`short`**|16-bit|Larger than byte, smaller than int.|
|**`int`**|32-bit|The standard (default) whole number type.|
|**`long`**|64-bit|Used for very large whole numbers.|

---

### **Important Assignment Rule**

While `int` handles most whole numbers, there is a specific requirement for the `long` type:

- **Long Suffix (`L`):** If a number is too large to be stored in an `int` (exceeding $2^{31}-1$), you **must** use the suffix `L` or `l` to explicitly tell the compiler the literal is a `long`.


> **Example:**
> `long population = 8000000000L; // Suffix L is required here`