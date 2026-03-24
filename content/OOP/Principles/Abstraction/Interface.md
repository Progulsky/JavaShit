---
tags:
  - "#java"
  - "#java_core"
  - OOP
  - interface
  - abstraction
---
# Interface

**Related notes:** [[Abstraction]], [[Functional_Interface]], [[Overriding]], [[Polymorphism]]

---

An **Interface** is a completely abstract type that defines a contract. It specifies **what** a class should do without dictates **how** it should do it. Interfaces allow Java to support multiple inheritance of type and are the cornerstone of decoupled, plug-and-play architectures.

---

### Core Concept & Implementation

Interfaces cannot be instantiated. Instead, they are "adopted" by classes (concrete, abstract, enum, or record) using the `implements` keyword.

- **Contract:** Any class implementing an interface must provide a body for its abstract methods.
    
- **Multiple Implementation:** Unlike classes, a single class can implement multiple interfaces, allowing it to take on multiple "roles."
    
- **Extension:** An interface cannot _implement_ another interface, but it can **extend** one or more interfaces.

```
public interface Animal {
    void eat(); // Implicitly public and abstract
}

public interface Pet {
    void play();
}

// Dog implements multiple interfaces
public class Dog implements Animal, Pet {
    @Override
    public void eat() { System.out.println("Dog eats."); }
    
    @Override
    public void play() { System.out.println("Dog plays."); }
}
```

---

### Interface Members

All variables in an interface are implicitly **`public static final`** (constants). Methods have evolved over different Java versions:

| **Method Type** | **Characteristics**                                                         | **Key Purpose**                                                 |
| --------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------- |
| **Abstract**    | No body; implicitly `public abstract`.                                      | Defines the mandatory contract for subclasses.                  |
| **Default**     | Uses `default` keyword; has a body. Implicitly public and can be overridden | Adds new methods to interfaces without breaking old code.       |
| **Static**      | Uses `static` keyword; has a body. Can be private                           | Provides utility methods belonging to the interface.            |
| **Private**     | Introduced in Java 9; can be `static`.                                      | Helper methods for shared logic between default/static methods. |

---

### Coding to an Interface

"Coding to an interface" is a design principle where variables and parameters use interface types rather than concrete class types.

**Why it matters:**

- **Flexibility:** You can swap a `PdfPrinter` for an `HtmlPrinter` without touching the `ReportPrinter` logic.
    
- **Testability:** You can easily inject "mock" objects during testing.
    
- **Decoupling:** Your high-level logic becomes independent of low-level implementation details.

```
// Good Practice: Dependency Injection with Interfaces
public class ReportPrinter {
    private Printer printer; // Depends on the abstraction

    public ReportPrinter(Printer printer) {
        this.printer = printer;
    }

    public void printReport(String report) {
        printer.print(report); // Works regardless of the specific Printer type
    }
}
```

---

### Why Use Interfaces?

1. **Polymorphism:** Treat different objects (Dog, Cat, Robot) as the same type (Actionable) if they implement the same interface.
    
2. **Multiple Inheritance:** Overcomes the "Diamond Problem" of class inheritance while allowing a class to satisfy multiple requirements.
    
3. **Standardization:** Enforces a consistent API across different parts of a large system.