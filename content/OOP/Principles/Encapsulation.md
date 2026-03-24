---
tags:
  - "#java"
  - "#java_core"
  - OOP
  - principle
---
# Encapsulation

**Related notes:** [[Class]], [[Field]], [[Method]]

---

**Encapsulation** is a core pillar of Object-Oriented Programming (OOP) that involves bundling data (fields) and the methods that operate on that data into a single unit, while restricting direct access to some of the object's components. It is the practice of hiding internal implementation details and exposing only a controlled interface to the outside world.

---

### Why Use Encapsulation?

- **Data Protection:** Prevents external code from corrupting the internal state of an object by modifying fields in unexpected ways.
    
- **Validation & Control:** Setters allow you to implement logic to ensure only valid data is assigned to your fields.
    
- **Flexibility & Maintenance:** You can change the internal implementation (e.g., changing a data type or calculation) without breaking the code that uses your class.
    
- **Modularity:** Leads to cleaner code by separating an object's external contract from its internal complexity.

---

### Implementation Strategy

You achieve encapsulation by following three standard steps:

1. **Restrict Access:** Mark all instance **fields** as `private`.
    
2. **Controlled Read:** Provide public **Getter** methods to allow external code to view the data.
    
3. **Controlled Write:** Provide public **Setter** methods to allow external code to update the data safely.

---

### Encapsulation Methods

#### Getters (Accessors)

A getter is a public method used to retrieve the value of a private field. It provides read-only access to the data.

```
private int age;

// Getter: Returns the value of age
public int getAge() {
    return age;
}
```

#### Setters (Mutators)

A setter is a public method used to update the value of a private field. This is where you include validation logic to protect the integrity of your object.

```
// Setter: Updates age only if the new value is valid
public void setAge(int age) {
    if (age > 0 && age < 120) {
        this.age = age; // 'this.age' refers to the field, 'age' refers to the parameter
    } else {
        System.out.println("Invalid age provided.");
    }
}
```

---

### Best Practices

- **Judicious Setters:** Not every field needs a setter. If a value should not change after the object is created, omit the setter to ensure the field remains **immutable**.
    
- **Defensive Copying:** When returning mutable objects (like lists or dates) via a getter, consider returning a copy to prevent the caller from modifying the internal object directly.