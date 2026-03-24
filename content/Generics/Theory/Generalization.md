---
tags:
  - "#java"
  - "#java_core"
  - generic
  - principle
---
# Generalization

**Related notes:** [[Class]], [[Inheritance]], [[Polymorphism]]

---

**Generalization** is a bottom-up design process where you identify common traits across multiple specific classes and move them into a single, broader **superclass**. It is effectively the "reverse" of specialization: instead of breaking a general concept down into specific types, you are grouping specific types under a general umbrella.

---

### Conceptual Flow

In software architecture, generalization focuses on the **"is-A"** relationship. By extracting shared behaviors and attributes, you create a hierarchy that simplifies the mental model of your system.

- **Specific Classes:** `Dog`, `Cat`, `Bird`.
    
- **Generalized Superclass:** `Animal` (containing shared traits like `eat()`, `sleep()`, and `age`).

---

### Implementation via Inheritance

In Java, generalization is achieved using the `extends` keyword (for classes) or the `implements` keyword (for interfaces).

```
// The Generalization: Parent class holding shared logic
class Vehicle {
    int wheels;
    
    void start() {
        System.out.println("Engine roaring...");
    }
}

// Specialization: Inheriting common features and adding unique ones
class Car extends Vehicle {
    int doors; // Unique to Car
}

class Bike extends Vehicle {
    boolean hasKickstand; // Unique to Bike
}
```

---

### Key Benefits

|**Benefit**|**Description**|
|---|---|
|**Code Reusability**|Common logic (like `start()`) is written once in the superclass rather than duplicated in every child.|
|**Centralized Maintenance**|Updating a method in the generalized class automatically applies the change to all subclasses.|
|**Architectural Clarity**|Organizes code into a logical hierarchy that mirrors real-world relationships.|
|**Polymorphic Power**|You can write methods that accept the generalized type (e.g., `void repair(Vehicle v)`), allowing them to work with any subclass.|

---

### Generalization vs. Abstraction

While they are related, they serve different purposes:

- **Abstraction** focuses on hiding complexity (the "how").
    
- **Generalization** focuses on finding commonality among different types (the "what's the same").

> **AI Insight:** Think of Generalization as a way to "dry out" your code (Don't Repeat Yourself). If you find yourself writing the same three fields in five different classes, you have a prime candidate for a generalized superclass.