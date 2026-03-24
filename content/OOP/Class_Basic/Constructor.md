---
tags:
  - "#java"
  - "#java_core"
  - OOP
  - class_member
---
# Constructor

**Related notes:** [[Class]], [[Object]], [[Field]], [[Overloading]]

---

A **Constructor** is a special method used to **initialize objects** at the moment of their creation. It establishes the initial state of an object by assigning values to its fields and executing any necessary setup logic.

### Key Rules

- **Naming:** Must have the exact same name as the class.
    
- **No Return Type:** Does not return any value, not even `void`.
    
- **Invocation:** Triggered automatically by the `new` keyword (e.g., `new Person()`).
    
- **Default Constructor:** If you do not define any constructor, Java provide a hidden, no-argument "default constructor" automatically.

---

### Implementation Example

```
public class Person {
    private String name;

    // Constructor definition
    public Person(String name) {
        this.name = name;
    }
}
```

---

### Constructor Chaining

**Constructor chaining** is the process of calling one constructor from another within the same class (or from a parent class). This practice centralizes initialization logic and minimizes code duplication.

To chain constructors in the same class, use the `this()` statement.

```
public class Car {
    private String model;
    private int year;

    // No-argument constructor
    public Car() {
        this("Unknown", 2000); // Chains to the parameterized constructor below
    }

    // Parameterized constructor
    public Car(String model, int year) {
        this.model = model;
        this.year = year;
    }
}
```

> **Crucial Constraints:**
> - The `this()` call must be the **first statement** in the constructor body.
> - You can only call **one** other constructor per constructor execution.

---

### Overloading

Like regular methods, constructors can be **overloaded**. You can provide multiple constructors as long as their parameter lists (number, type, or order of arguments) are unique. This allows you to create objects in various ways depending on the data available.