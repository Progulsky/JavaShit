---
tags:
  - "#java"
  - "#java_core"
  - functional
  - interface
---
# Functional_Interface

**Related notes:** [[Lambda_Expression]], [[Method_References]], [[Interface]], [[Built-in_Functional_Interfaces]]

---

A **Functional Interface** is a specialized interface that contains **exactly one abstract method**. They are the foundation of functional programming in Java, serving as the "blueprint" for Lambda Expressions and Method References.

---

### The @FunctionalInterface Annotation

While not strictly required, the `@FunctionalInterface` annotation is a best practice. It acts as a safety net:

- **Validation:** It tells the compiler to verify that the interface truly has only one abstract method.
    
- **Clarity:** It explicitly communicates the interface's purpose to other developers.
    
- **Prevention:** If someone accidentally tries to add a second abstract method, the code will fail to compile.

---

### What Can They Contain?

Despite the "one abstract method" rule, functional interfaces are surprisingly flexible. They can include:

1. **Exactly One Abstract Method:** This is the core requirement (the Single Abstract Method, or SAM).
    
2. **Any Number of Default Methods:** Since default methods have a body, they do not count against the "one abstract method" limit.
    
3. **Any Number of Static Methods:** Like default methods, these do not count as abstract.
    
4. **Methods from the Object Class:** Overriding public methods from `java.lang.Object` (like `equals(Object)` or `toString()`) does not count toward the limit.

---

### Implementation: From Classes to Lambdas

Before functional programming was added to Java, you had to use **Anonymous Inner Classes** to implement these interfaces. Today, you can use **Lambdas** for much cleaner code.

```
// 1. The Interface Definition
@FunctionalInterface
public interface Greeter {
    void sayHello(String name);
}

// 2. Old Way: Anonymous Inner Class
Greeter oldWay = new Greeter() {
    @Override
    public void sayHello(String name) {
        System.out.println("Hello, " + name);
    }
};

// 3. New Way: Lambda Expression
Greeter modernWay = (name) -> System.out.println("Hi, " + name);

modernWay.sayHello("Developer");
```

---

### Why Use Functional Interfaces?

- **Lambda Support:** They are the only types that can be target types for lambda expressions.
    
- **Stream API:** Most operations in the Java Stream API (like `.filter()` or `.map()`) rely on the standard functional interfaces.
    
- **Cleaner APIs:** They allow you to pass behavior (logic) as a parameter to methods.