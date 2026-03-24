---
tags:
  - "#java"
  - "#java_core"
  - class
  - class_subtype
  - nested
---
# Anonymous_Class

**Related notes:** [[Class]], [[Inner_Class]], [[Static_Nested_Class]], [[Local_Class]], [[Statement]], [[Lambda_Expression]]

---

An **anonymous class** is an inner class without a name that allows for simultaneous declaration and instantiation. They are ideal for "one-off" implementations where creating a separate `.java` file for a subclass or interface implementation would be unnecessary overhead.

---

### How It Works

Anonymous classes are defined directly within an expression as a specialized type of local inner class. Because they lack a name, they cannot have a custom constructor; they rely instead on the parent class's constructor or the interface definition.

```
ParentType objectName = new ParentType() {
    // Override methods or add logic here
    @Override
    public void someMethod() {
        System.out.println("Implementation here!");
    }
};
```

---

### Types of Anonymous Classes

- **Extending a Class:** You can create a subclass of an existing class — including abstract classes — on the fly.

```
    Thread t = new Thread() {
        public void run() {
            System.out.println("Child Thread Running");
        }
    };
    t.start();
```

- **Implementing an Interface:** This is the most common use case, frequently used for event listeners or functional requirements.

```
    Runnable r = new Runnable() {
        @Override
        public void run() {
            System.out.println("Running via Interface");
        }
    };
```

---

### Key Characteristics

- **No Name:** Since it has no identifier, you cannot define a custom constructor.
    
- **Single Use:** Designed for a specific, immediate task; it cannot be reused elsewhere in the code.
    
- **Variable Access:** It can access members of its enclosing class and local variables from its definition scope, provided they are **effectively final** (their value does not change after initialization).
    
- **Compiled Name:** The compiler assigns a name for the bytecode, typically following the pattern `OuterClass$1.class`.
    
- **Scope:** It creates its own scope; the `this` keyword refers specifically to the anonymous class instance, not the outer class.