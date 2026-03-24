---
tags:
  - "#java"
  - "#java_core"
  - OOP
  - class_member
  - method
  - abstraction
---
# Abstract_Method

**Related notes:** [[Method]], [[Abstraction]], [[Interface]], [[Overriding]], [[Polymorphism]]

---

An **abstract method** is a method declared without an implementation—it contains no method body, only a signature. It serves as a placeholder, signaling that a behavior exists but leaving the specific details to be defined by subclasses.

---

### Key Characteristics

- **The `abstract` Keyword:** Must be explicitly declared using the `abstract` modifier.
    
- **No Method Body:** The declaration must end with a semicolon (`;`) instead of curly braces (`{}`).
    
- **Strict Container Rules:** An abstract method can only reside within an **Abstract Class** or an **Interface**.
    
- **Mandatory Implementation:** Any concrete (non-abstract) subclass that inherits from the abstract class **must** provide a body for all inherited abstract methods.

---

### Purpose and Utility

- **Defining a Contract:** Establishes a common set of rules that all subclasses must follow, ensuring consistency across different implementations.
    
- **Enforcing Structure:** Forces developers to think about specific behaviors (like `makeSound`) while allowing them the freedom to decide how those behaviors are performed.
    
- **Achieving Abstraction:** Hides the complexity of implementation by allowing you to interact with objects at a high level.
    
- **Framework Design:** Widely used in APIs and frameworks to define hooks or event handlers that the user must implement.

---

### Implementation Example

```
abstract class Shape {
    // Abstract method: Every shape has an area, 
    // but the formula depends on the specific shape.
    abstract double calculateArea(); 
}

class Circle extends Shape {
    private double radius;

    public Circle(double radius) {
        this.radius = radius;
    }

    @Override
    double calculateArea() {
        return Math.PI * radius * radius;
    }
}
```