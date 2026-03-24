---
tags:
  - "#java"
  - "#java_core"
  - OOP
  - class_member
---
# Field

**Related notes:** [[Class]], [[Variable]], [[Scope]]

---

**Fields** (also known as **instance variables**, **class variables**, or **attributes**) are variables declared inside a class but outside any method, constructor, or block. They represent the **state** or **properties** of an object.

---

### Key Features of Fields

- **Scope:** They belong to the class itself, making them accessible to all methods within that class.
    
- **Lifecycle:** Instance fields exist as long as the object exists in memory.
    
- **Automatic Initialization:** Unlike local variables, fields are assigned **default values** if not explicitly initialized:
    
    - **Booleans:** `false`
        
    - **Integers (byte, short, int, long):** `0`
        
    - **Floating-point (float, double):** `0.0`
        
    - **Reference Types (Objects):** `null`
        
- **Modifiers:** They can be configured using keywords like `private`, `public`, `static`, or `final`.
    
- **Timing:** They are initialized immediately before the constructor is executed.

> **Note:** Fields with **primitive types** can never be `null`; they will always hold a default numeric or boolean value.

---

### Types of Fields

#### 1. Instance Fields

Instance fields belong to a specific **object**. Memory is only allocated when an object is created, and every instance maintains its own separate copy of the variable.

- **Access:** via `objectName.fieldName`.
    
- **Behavior:** Changing the value in one object does not affect other objects of the same class.


```
class Dog {
    private String name; // instance field

    public Dog(String name) {
        this.name = name;
    }

    public void printName() {
        System.out.println("name = " + name);
    }
}

// Usage: rex and fluffy have unique names
Dog rex = new Dog("Rex");
Dog fluffy = new Dog("Fluffy");
rex.printName();    // Outputs: Rex
fluffy.printName(); // Outputs: Fluffy
```

#### 2. Static Fields

Static fields belong to the **Class** itself, rather than any individual object. All instances of the class share exactly one copy of the variable.

- **Access:** via `ClassName.fieldName`. An instance is not required.
    
- **Keyword:** `static`.
    
- **Common Uses:** Constants (e.g., `Math.PI`), counters, or shared resource management.

```
class Dog {
    private static String name; // shared static field

    public Dog(String name) {
        Dog.name = name; // Updating the shared class variable
    }

    public void printName() {
        System.out.println("name = " + name);
    }
}

// Usage: The last assignment overwrites the shared value
Dog rex = new Dog("Rex");
Dog fluffy = new Dog("Fluffy"); 
rex.printName();    // Outputs: Fluffy (shared value was changed!)
fluffy.printName(); // Outputs: Fluffy
```

---

### OOP Rule: Class Fields vs. Local Variables

- **Class Fields (Global State):** Use only for permanent object characteristics (e.g., `root`, `size`).
    
- **Local Variables (Execution State):** Use for temporary data during method execution (e.g., current traversal node).
    
- **The Danger:** Using fields for temporary execution steps corrupts global data (like overwriting `root`), breaks recursion by sharing state across the Call Stack, and destroys thread-safety.