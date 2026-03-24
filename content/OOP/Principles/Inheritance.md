---
tags:
  - "#java"
  - "#java_core"
  - OOP
  - principle
---
# Inheritance

**Related notes:** [[Class]], [[Method]], [[Overriding]]

---

**Inheritance** is a pillar of Object-Oriented Programming (OOP) that allows a **subclass** (child) to acquire the fields and methods of a **superclass** (parent). It facilitates code reusability and establishes a hierarchical "is-A" relationship between classes.

---

### Core Principles

- **The `extends` Keyword:** Used to create a subclass that inherits from a superclass.
    
- **Code Reuse:** Subclasses automatically gain access to non-private members of the parent, reducing redundancy.
    
- **Single Inheritance:** In Java, a class can have multiple subclasses, but a subclass can **only extend one** parent class (to prevent complexity and the "Diamond Problem").

```
class Animal {
    void speak() {
        System.out.println("Animal speaks");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Dog barks");
    }
}

// Dog 'is-A' Animal, so it can use speak() and bark()
Dog myDog = new Dog();
myDog.speak(); 
myDog.bark();
```

---

### The `super` Keyword

The `super` keyword is a reference variable used to refer to immediate parent class objects. It is essential when a subclass overrides a method or shadows a field and you need to access the parent's version.

#### 1. Constructor Chaining

When a subclass is instantiated, it must first initialize its parent state.

- If you don't call `super()`, Java automatically inserts a call to the parent's default (no-arg) constructor.
    
- If the superclass lacks a default constructor, you **must** explicitly call `super(...)` with the required arguments.

> **Rule:** `super()` must be the **first statement** in a subclass constructor. Consequently, you cannot use `this()` and `super()` in the same constructor.

```
class Animal {
    Animal(String name) {
        System.out.println("Animal: " + name);
    }
}

class Dog extends Animal {
    Dog() {
        super("Dog");  // Mandatory explicit call to parent constructor
        System.out.println("Dog instance created");
    }
}
```

#### 2. Accessing Methods and Fields

`super` allows you to trigger parent logic within an overridden method or access parent fields that have been "shadowed" (redeclared) in the child.

```
class Cat extends Animal {
    @Override
    void sound() {
        super.sound();  // Executes parent logic
        System.out.println("Cat meows");
    }
}
```

---

### Access Control: The `protected` Modifier

While `private` members are not inherited, marking fields or methods as **`protected`** allows subclasses to access them directly while still keeping them hidden from the rest of the application.