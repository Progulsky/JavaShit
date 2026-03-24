---
tags:
  - "#java"
  - "#java_core"
  - fundamentals
  - variable
  - type_system
---
# Var

**Related notes:** [[Variable]], [[Type_Inference]], [[Target_Typing]]

---

Introduced in Java 10, `var` is a reserved type name that allows the compiler to infer the data type based on the assigned value. This feature, known as **Local Variable Type Inference**, simplifies code by letting the Java compiler determine the specific type at compile time.

---

### Usage Examples

```
var name = "Alice";           // Inferred as String
var age = 30;                // Inferred as int
var list = new ArrayList<>(); // Inferred as ArrayList<Object>
```

---

### Rules of Engagement

| **Allowed Usage**                                                 | **Prohibited Usage**                                                                             |
| ----------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| **Local variables** inside methods, constructors, or code blocks. | **Class fields** (neither instance nor static variables).                                        |
| **Loop variables** in for-each or classic `for` loops.            | **Method parameters** or **return types**.                                                       |
| **Object references** to any valid Java object.                   | **Lambda expression** parameters (if mixing it with other types)                                 |
| **Try-with-resources** variables.                                 | **Variables without immediate initialization** (the compiler needs the value to infer the type). |

---

### Key Benefits

- **Reduces Boilerplate:** Greatly simplifies declarations, especially when dealing with complex **Generics** like `Map<String, List<User>>`.
    
- **Improves Readability:** Shifts the focus toward the variable's name and purpose rather than its implementation details.
    
- **Maintainability:** Makes it easier to change the specific implementation (e.g., changing from `ArrayList` to `LinkedList`) without updating the type on the left side of the assignment.


---

### Critical Constraints

1. **Compile-Time Only:** Java remains a **statically typed** language. Once the compiler determines the type of a `var`, it is fixed and cannot change (e.g., you cannot assign an `int` to a `var` that was inferred as a `String`).
    
2. **Explicit Initialization:** You cannot write `var x;`. Because the type is inferred from the assigned value, the variable **must** be initialized at the moment of declaration.
    
3. **Null Assignment:** You cannot initialize a `var` with `null` alone (e.g., `var x = null;` is invalid) because the compiler cannot determine which object type the variable should be.
