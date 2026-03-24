---
tags:
  - "#java"
  - "#java_core"
  - OOP
  - method
---
# Overloading

**Related notes:** [[Method]], [[Constructor]]

---

**Method Overloading** allows a class to have multiple methods with the same name, provided their parameter lists are different. It is a powerful feature that increases code readability and allows for similar logic to be applied to different data types or varying amounts of input.

---

### The Method Signature

In Java, a method's uniqueness is determined by its **signature**. A signature consists only of the **method name** and the **parameter list** (the number, types, and order of parameters).

> **What does NOT count:**
> 
> - **Return Type:** Changing the return type while keeping the same parameters is not allowed.
>     
> - **Parameter Names:** The compiler ignores the names you give to variables; it only cares about their types.
>     
> - **Exceptions:** Throwing different exceptions does not make a signature unique.

```
public int sum(int a, int b) { return a + b; }

// Valid: Different parameter types
public double sum(double a, double b) { return a + b; }

// Valid: Different number of parameters
public int sum(int a, int b, int c) { return a + b + c; }

// INVALID: Only return type differs
// public double sum(int a, int b) { ... } 
```

---

### Best Practices

- **Consistency:** Only use overloading for methods that perform the same conceptual task.
    
- **Clarity:** Avoid overloading where the parameter types are too similar (like `int` and `long`), as this can lead to ambiguity and make the code harder to maintain.