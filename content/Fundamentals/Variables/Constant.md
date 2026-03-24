---
tags:
  - "#java"
  - "#java_core"
  - fundamentals
  - variable
  - immutability
  - static
---
# Constant

**Related notes:** [[Variable]], [[Enum]]

---

**Constants** are fixed values that cannot be changed once they are assigned. They are used for values that remain logically consistent throughout a program, such as mathematical constants (e.g., PI), configuration limits (e.g., maximum number of users), or predefined settings like status codes.

---

### Creating Constants

In Java, constants are typically defined using a combination of keywords and naming conventions:

- **`final`**: This keyword ensures the **variable's** value cannot be modified after its initial assignment.
    
- **`static`**: This ensures there is only one copy of the value shared across all instances of the **class**.

**Standard Syntax:**

```
static final <type> NAME = value;
```

---

### Key Rules and Characteristics

| **Rule**               | **Description**                                                                                                                                                                            |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Initialization**     | Must be initialized exactly once—either during declaration or in a **constructor**. (Static constants must be initialized in a static block if not at declaration).                        |
| **Immutability**       | Once initialized, the value cannot be reassigned.                                                                                                                                          |
| **Data Types**         | Can be of any type, including **primitive** types or reference types                                                                                                                       |
| **Optimization**       | If a value is a compile-time constant (e.g., `static final int X = 5;`), the compiler replaces all occurrences of `X` with the literal value `5`.                                          |
| **Instance Constants** | Non-static `final` variables act as constants for a specific object; while the value is fixed for that object, different objects can have different values assigned to that variable once. |
