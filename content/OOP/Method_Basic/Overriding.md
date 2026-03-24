---
tags:
  - "#java"
  - "#java_core"
  - OOP
  - method
---
# Overriding

**Related notes:** [[Method]], [[Inheritance]], [[Polymorphism]], [[Class]], [[Interface]], [[Annotation]]

---

**Method Overriding** occurs when a subclass (child class) provides a specific implementation for a method that is already defined in its superclass (parent class). It is a core feature of **Polymorphism**, allowing a subclass to inherit a method's signature while customizing its behavior.

---

### Use Cases

- **Specialized Behavior:** Implementing logic that is unique to a subclass (e.g., a `Dog` class providing a specific sound).
    
- **Framework Integration:** Overriding lifecycle methods in frameworks like Spring or Android.
    
- **Functional Extension:** Using the `super` keyword to execute the parent's logic while adding additional steps.

---

### Key Rules for Overriding

To successfully override a method, the subclass version must adhere to the following:

1. **Identical Signature:** Must have the same name and the exact same parameter list.
    
2. **Compatible Return Type:** The return type must be the same or a "covariant" type (a subclass of the original return type).
    
3. **Access Modifiers:** The subclass method cannot be _more_ restrictive than the parent (e.g., if the parent is `protected`, the child must be `protected` or `public`).
    
4. **The `@Override` Annotation:** While optional, using this annotation is a best practice. It tells the compiler to verify that you are actually overriding a method, preventing silent errors caused by typos.

---

### Implementation Example

```
class Animal {
    void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        // Option 1: Complete replacement
        System.out.println("Dog barks");
        
        // Option 2: Call parent and extend
        // super.sound();
        // System.out.println("...and then the dog barks");
        
        // Option 3: Call parent
        // super.sound();
    }
}
```

---

### What Cannot Be Overridden?

Certain methods are protected from being modified by subclasses:

- **Final Methods:** If a method is marked `final`, it cannot be overridden.
    
- **Static Methods:** These belong to the class, not the instance. Declaring a static method with the same name in a child class is called **Method Hiding**, not overriding.
    
- **Private Methods:** These are not visible to subclasses, so they cannot be overridden.
    
- **Constructors:** These are unique to their specific class and are not inherited.