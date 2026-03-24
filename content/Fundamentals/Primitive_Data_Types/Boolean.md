---
tags:
  - "#java"
  - "#java_core"
  - fundamentals
  - primitives
---
# Boolean

**Related notes:** [[Primitive_Data_Types]], [[Wrapper_Class]]

---

The **Boolean** is a **Primitive** data type in Java used to represent logical values. It is the simplest data type, focusing purely on truth-functional logic.

---

### **Core Characteristics**

- **Keyword:** It uses the `boolean` **Keyword**.
    
- **Logical States:** It represents exactly two possible states: **`true`** or **`false`**.
    
- **Default Value:** If a boolean instance variable is declared but not initialized, its default value is **`false`**.

---

## Usage and Behavior

Boolean values are primarily used for conditional checks and flow control in programs.

|**Feature**|**Description**|
|---|---|
|**Logic**|Primarily used with `if` statements, `while` loops, and logical operators.|
|**Size**|While the size is not precisely defined by the Java Virtual Machine (JVM) specification, it represents 1 bit of information.|
|**Assignment**|Can only be assigned the literals `true` or `false`.|

```
boolean isJavaFun = true;
boolean isFishTasty = false;

if (isJavaFun) {
    System.out.println("Keep learning!");
}
```