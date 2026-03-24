---
tags:
  - "#java"
  - "#java_core"
  - OOP
  - class_member
---
# Object

**Related notes:** [[Class]], [[Field]], [[Method]], [[Constructor]]

---

An **Object** is a concrete instance of a particular class. If a **class is the blueprint**, then an **object is the actual building** constructed from that blueprint—complete with real data and functional behavior.

The process of creating an object is known as **instantiation**. You can generate numerous unique objects from a single class, each maintaining its own distinct state.

---

### Core Characteristics

- **State:** The data stored within the object's **fields**.
    
- **Behavior:** The actions the object can perform, defined by its **methods**.
    
- **Identity:** Each object has a unique presence in memory, even if its state is identical to another object's.
    
- **Isolation:** Every object possesses its own copy of the class’s instance (non-static) fields.

---

### Instantiating an Object

To create an object, you must use the `new` keyword followed by the class constructor.

```
Car myCar = new Car(); 
```

- `new`: Allocates memory for the new object.
    
- `Car()`: Invokes the constructor to initialize the object.
    
- `myCar`: Acts as a **reference variable** that stores the memory address of the object.

#### Initialization Safety

1. **Uninitialized Variables:** Attempting to use a local object variable without initialization triggers a **compile-time error**.
    
2. **Null References:** Assigning `null` to a variable means it points to "nothing." Accessing members of a `null` reference results in a runtime **NullPointerException**.

---

### Reference Semantics

Object variables do not store the object itself; they store a **reference** (a memory address). If you assign one object variable to another, both variables will point to the exact same object in memory.

```
Person a = new Person();
a.name = "Alice";

Person b = a;  // 'b' now points to the same memory address as 'a'
b.name = "Bob";

System.out.println(a.name); // Output: Bob (because both references modified the same object)
```

---

### The `this` Keyword

The `this` keyword refers to the **current instance** of the class. It is essential for resolving ambiguity and enabling specific design patterns.

#### 1. Passing the Current Object

You can pass the current instance as an argument to other methods or classes.

```
public void register() {
    Database.save(this); // Passes the current object to a save method
}
```

#### 2. Returning the Current Object (Method Chaining)

Returning `this` allows you to string multiple method calls together in a single statement, often referred to as a **Fluent API**.

```
public class Person {
    private String name;

    public Person setName(String name) {
        this.name = name;
        return this; // Returns the current instance
    }
}

// Usage: Method Chaining
Person p = new Person().setName("Alice");
```