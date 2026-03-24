---
tags:
  - "#java"
  - "#java_core"
  - class
  - class_subtype
  - nested
  - static
---
# Static_Nested_Class

**Related notes:** [[Class]], [[Inner_Class]], [[Local_Class]], [[Anonymous_Class]]

---

In Java, classes can be defined within other classes. When a nested class is declared with the `static` modifier, it is known as a **Static Nested Class**.

Technically, it is not considered an "inner class" (a term reserved for non-static nested classes). Instead, it behaves like a top-level class that has been packaged inside another class for organizational convenience.

---

### Key Characteristics

- **No Instance Link:** A static nested class does not hold a reference to an instance of the outer class. Consequently, it cannot access the outer class's instance variables or methods.
    
- **Access Rules:** It can only access **static** members of the outer class (including private ones). Conversely, the outer class can access all components of the static nested class, including private ones.
    
- **Independent Instantiation:** You do not need to instantiate the outer class to create an instance of the static nested class.
    
- **Namespace:** It is referenced using the outer class's name: `OuterClass.StaticNestedClass`.
    
- **Implicitly Static Types:** In Java, nested **Records**, **Enums**, and **Interfaces** are implicitly static, regardless of whether the `static` keyword is explicitly used.

---

### Syntax and Implementation

```
public class OuterClass {
    private static String staticValue = "Static Data";
    private String instanceValue = "Instance Data";

    // Static Nested Class
    public static class StaticNested {
        public void display() {
            // Success: Can access static members of OuterClass
            System.out.println("Accessing: " + staticValue);

            // Error: CANNOT access instance members directly
            // System.out.println(instanceValue); 
        }
    }
}

// Instantiation
public class Main {
    public static void main(String[] args) {
        // Accessing the class directly via the OuterClass name
        OuterClass.StaticNested nested = new OuterClass.StaticNested();
        nested.display();
    }
}
```

---

### Why Use Static Nested Classes?

- **Logical Grouping:** If a class is only useful to one specific class, nesting them keeps the package structure clean and indicates a clear relationship.
    
- **Enhanced Encapsulation:** It allows a helper class to access private static members of the outer class without exposing those members to the entire package.
    
- **Readability and Maintenance:** Keeping related logic in one place makes the codebase easier to navigate and maintain.