---
tags:
  - "#java"
  - "#java_core"
  - OOP
  - class
---
# Class

**Related notes:** [[Field]], [[Object]], [[Constructor]], [[Method]], [[Code_Block]], [[Scope]]

---

A **Class** is the fundamental building block of Java applications. It functions as a **template** or blueprint for creating objects, defining a custom data type that encapsulates both state and behavior.

Think of a class as an **empty form**: it specifies what information an object will hold and what it can do, but it doesn't store actual data until you instantiate an **object** (an instance) from it.

---

### Implementation Example

To define a class, you use the `class` keyword followed by its members.

```
public class Car {
    // Fields (State)
    String brand;
    int year;

    // Method (Behavior)
    void drive() {
        System.out.println(brand + " is driving.");
    }
}

// Usage
public class Main {
    public static void main(String[] args) {
        Car myCar = new Car();       // Create an object instance
        myCar.brand = "Toyota";      // Set field value
        myCar.year = 2020;
        myCar.drive();               // Call method
    }
}
```

---

### Class Members

Class members are the internal components that define the class's structure and capabilities.

- **Fields (Attributes):** Variables used to store data specific to each object.
    
- **Methods (Actions):** Blocks of code that define the logic and operations an object can perform.

---

### Why Use Classes?

- **Logical Organization:** Group related data and logic into a single unit.
    
- **Reusability:** Write code once in a class and create as many objects as needed.
    
- **Scalability:** Easily build complex systems by combining different classes.
    
- **OOP Foundations:** Classes are essential for implementing core principles like **Inheritance**, **Polymorphism**, and **Encapsulation**.