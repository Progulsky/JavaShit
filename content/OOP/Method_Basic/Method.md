---
tags:
  - "#java"
  - "#java_core"
  - OOP
  - class_member
  - method
---
# Method

**Related notes:** [[Class]], [[Object]], [[Overloading]], [[Overriding]], [[Varargs]], [[Code_Block]], [[Scope]]

---

A **Method** is a structured block of code designed to perform a specific task. It can be invoked by name, typically accepting a fixed number of parameters (arguments), and can be executed multiple times to produce results based on the input or the program's state.

Methods that return a value can be used within **expressions**, while any method call can serve as a standalone **statement**. Every method maintains its own unique **scope**.

---

### Anatomy of a Method

- **Modifier:** Defines the access level (e.g., `public`, `private`).
    
- **Return Type:** Specifies the data type of the value the method sends back.
    
- **Method Name:** A unique identifier used to call the method.
    
- **Parameters:** Optional variables that receive input (arguments).
    
- **Method Body:** The code block containing the logic to be executed.

#### Declaration vs. Call

To **declare** a method, you define all its parts within a class. To **call** (invoke) a method, you use its name followed by the necessary arguments in parentheses.

```
// Declaration
public int add(int a, int b) {
    return a + b;
}

// Call
int result = add(10, 20); 
```

---

### The `return` Statement

The `return` statement passes a calculated value back to the caller.

- A method must declare a return type (e.g., `int`, `String`), and the returned value must match that type.
    
- A `return` statement is required in **every possible execution path** (e.g., inside `if/else` blocks).
    
- **Void Methods:** Use the `void` keyword if no value is returned. While not required, `return;` can be used in void methods for an early exit.

---

### Parameters vs. Arguments

- **Parameter:** A variable listed in the method declaration (the "placeholder").
    
- **Argument:** The actual value (literal or variable) passed to the method during a call.
    

> **Constraint:** The number and types of arguments provided during a call must exactly match the method’s defined parameters.

---

### Method Chaining

Method chaining allows you to invoke multiple methods in a single statement. This is achieved by having each method return an object reference (often `this`), allowing the next call to be appended immediately.

```
String result = "   Hello World   "
    .strip()
    .toUpperCase()
    .substring(0, 5); // Returns "HELLO"
```

---

### Instance vs. Static Methods

#### 1. Instance Methods

These belong to a specific **Object**. They require an object instance to be created before they can be called.

- **Access:** Can access both instance and static fields/methods directly.
    
- **Usage:** Use when the task depends on the specific state of an object.

#### 2. Static Methods

These belong to the **Class** itself. They can be invoked without creating an instance.

- **Keyword:** `static`.
    
- **Access:** Can only access other static members; they **cannot** access instance variables or use the `this` or `super` keywords.
    
- **Usage:** Ideal for utility functions (e.g., `Math.max()`).

```
// Static Call
int result = MathUtils.square(5);

// Instance Call
Car myCar = new Car();
myCar.drive();
```