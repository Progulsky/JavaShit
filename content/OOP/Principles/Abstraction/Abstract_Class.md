---
tags:
  - "#java"
  - "#java_core"
  - OOP
  - class
  - class_subtype
  - abstraction
---
# Abstract_Class

**Related notes:** [[Class]], [[Abstraction]], [[Polymorphism]], [[Inheritance]], [[Overriding]]

---

An **abstract class** is a specialized type of class that serves as a blueprint for other classes. Its primary restriction is that it **cannot be instantiated** directly; you cannot use the `new` keyword to create an object of an abstract class. Instead, it is designed to be inherited, providing a shared foundation of fields and methods while delegating specific details to its subclasses.

---

### Implementation Example

Abstract classes allow you to mix implemented logic (**concrete methods**) with empty signatures (**abstract methods**) that subclasses are forced to complete.

```
abstract class Animal {
    String name;

    Animal(String name) {
        this.name = name;
    }

    // Abstract method: No body, must be implemented by subclasses
    abstract void makeSound();

    // Concrete method: Shared implementation for all subclasses
    void sleep() {
        System.out.println(name + " is sleeping.");
    }
}

class Dog extends Animal {
    Dog(String name) {
        super(name);
    }

    @Override
    void makeSound() {
        System.out.println("Woof!");
    }
}

// Usage
Dog dog = new Dog("Buddy");
dog.makeSound(); // Outputs: Woof!
dog.sleep();     // Outputs: Buddy is sleeping.
```

---

### Key Features

- **No Direct Instantiation:** Attempting `new Animal()` results in a compilation error.
    
- **Abstract Methods:** Methods marked with `abstract` have no body. They act as a "contract" that any non-abstract subclass **must** fulfill.
    
- **Concrete Capabilities:** Unlike interfaces (traditionally), abstract classes can have regular methods with full logic and instance fields to maintain state.
    
- **Constructors:** They can have constructors. While they can't be called to make an `Animal`, they are executed when a `Dog` is created to initialize inherited fields.
    
- **Inheritance Flexibility:** An abstract class can extend another abstract class without implementing its methods. However, the first "concrete" class down the chain must implement **all** pending abstract methods from the entire hierarchy.

---

### Why Use Abstract Classes?

1. **Templates:** Create a common skeleton for a group of related classes.
    
2. **Enforced Contracts:** Ensure that all subclasses provide specific functionality (like `makeSound`) without defining exactly _how_ it works at the base level.
    
3. **Code Reuse:** Share common fields (like `name`) and methods (like `sleep`) once in the base class to avoid duplication across multiple subclasses.