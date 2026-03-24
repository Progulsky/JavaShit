---
tags:
  - "#java"
  - "#java_core"
  - fundamentals
  - metadata
---
# Keyword

**Related notes:** [[Token]], [[Primitive_Data_Types]], [[Conditional Logic]], [[Loop]], [[Class]], [[Object]], [[Method]], [[Variable]], [[Modifier]], [[Exception]]

---

**Keywords** (also known as **Reserved Words**) are predefined, reserved identifiers that have a specific, fixed meaning to the Java compiler. They act as the "building blocks" of the language's syntax and cannot be redefined for any other purpose.

---

## The "Golden Rule" of Keywords

> **Strictly Forbidden:** Keywords cannot be used as **Variable** names, **Method** names, **Class** names, or any other identifier.
> 
> _Example:_ `int public = 10;` will result in a compilation error because `public` is a reserved keyword.

---

## List of Popular Keywords

Java keywords are organized into functional groups that define the structure and behavior of your code.

|**Category**|**Keywords**|
|---|---|
|**Data Types**|`int`, `double`, `char`, `boolean`, `long`, `short`, `byte`, `float`|
|**Control Flow**|`if`, `else`, `switch`, `case`, `for`, `while`, `do`, `break`, `continue`, `default`|
|**Modifiers**|`public`, `private`, `protected`, `static`, `final`, `abstract`, `synchronized`, `volatile`|
|**Class/Object**|`class`, `interface`, `extends`, `implements`, `new`, `this`, `super`, `instanceof`|
|**Exception Handling**|`try`, `catch`, `finally`, `throw`, `throws`, `assert`|
|**Other Essentials**|`return`, `void`, `package`, `import`, `native`, `transient`|

---

## Key Technical Details

#### **1. Case Sensitivity**

All Java keywords are written in **lowercase**. For example, `While` or `WHILE` are not keywords, but using them as variable names is considered poor practice as it leads to confusion.

#### **2. Keywords vs. Reserved Literals**

While often grouped with keywords, `true`, `false`, and `null` are technically **literals** (values). However, they are still **reserved**, meaning you cannot use them as identifiers for variables or methods.

---

> **Official Resource:** For a complete, technical list of all keywords, you can refer to the [Java Language Specification (JLS)](https://docs.oracle.com/javase/specs/jls/se17/html/jls-3.html#jls-3.9).