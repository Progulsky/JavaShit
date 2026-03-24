---
tags:
  - "#java"
  - "#java_core"
  - OOP
  - principle
---
# Polymorphism

**Related notes:** [[Class]], [[Method]], [[Overriding]]

---

**Polymorphism** is the ability of an object to take on many forms. In programming, it allows a single interface or method name to be used for a general class of actions, where the specific action is determined by the exact nature of the object involved. It follows the principle of "one interface, many implementations."

---

### Why Use Polymorphism?

- **Code Reusability:** Write generic code that can process objects of different types as long as they share a common parent or interface.
    
- **Scalability:** Add new subclasses without needing to rewrite the existing logic that handles the superclass.
    
- **Flexibility:** Easily swap out behavior at runtime depending on the specific object being referenced.
    
- **Maintainability:** Promotes a clean architecture by decoupling high-level logic from specific implementation details.

---

### Types of Polymorphism

#### 1. Compile-time Polymorphism (Static Binding)

This occurs during the compilation phase and is achieved through **Method Overloading**. The compiler determines which method to call based on the number and types of arguments provided.

```
public class Calculator {
    public int add(int a, int b) { return a + b; }
    public double add(double a, double b) { return a + b; }
}
```

#### 2. Runtime Polymorphism (Dynamic Binding)

This happens during execution and is achieved through **Method Overriding**. A subclass provides its own version of a method already defined in its parent. Java decides which version to execute based on the actual object in memory, not the variable type.

```
Animal a = new Dog();
a.speak();  // Output: Dog barks (even though the reference is 'Animal')
```

---

### Compile-Time vs. Run-Time

|**Feature**|**Compile Time**|**Run Time**|
|---|---|---|
|**When it happens**|During compilation (`javac`)|During execution (JVM)|
|**Detection**|Syntax, type mismatches, missing methods|Logic errors, Nulls, bad input|
|**Logic**|Static binding (Overloading)|Dynamic binding (Overriding)|

---

### Understanding Types and `instanceof`

#### Compile-Time Type vs. Run-Time Type

- **Compile-time Type:** The declared type of the variable. The compiler uses this to check if a method call is legal.
    
- **Run-time Type:** The actual type of the object stored on the heap. This determines which overridden method is executed.

```
Movie movie = new Comedy("Airplane");
// Compile-time type: Movie
// Run-time type: Comedy
```

#### The `instanceof` Operator

The `instanceof` operator tests whether an object belongs to a specific class, subclass, or interface. It returns a boolean and is primarily used to ensure a safe **downcast** (converting a parent reference back to a child type).

```
if (a instanceof Dog d) {
    // Pattern matching: 'd' is automatically cast if the check passes
    d.bark(); 
}
```

> **Note:** When using `instanceof` in a series of checks, always test for the **most specific** subclasses first to ensure the logic doesn't trigger prematurely for a broader parent class.