---
tags:
  - "#java"
  - "#java_core"
  - generic
  - type_system
---
# Type_Argument

**Related notes:** [[Generic]], [[Type_Parameter]]

---

A **Type Argument** is the concrete, actual type you provide when you instantiate a generic class, implement a generic interface, or call a generic method.

Think of it this way: the **Type Parameter** is the "variable" in the definition, and the **Type Argument** is the "value" you assign to it during use.

---

### The Difference: Parameter vs. Argument

|**Term**|**Role**|**Context**|**Example**|
|---|---|---|---|
|**Type Parameter**|The placeholder / label|Class/Method **Definition**|`class Box<T>`|
|**Type Argument**|The actual class name|Class/Method **Usage**|`new Box<String>()`|

---

### Implementation Contexts

#### 1. In Generic Classes

When you create an object of a generic class, you must provide a type argument (unless you are using raw types, which is discouraged).

```
// 'T' is the Type Parameter
class Box<T> { 
    private T item;
}

// 'Integer' is the Type Argument
Box<Integer> myBox = new Box<>(); 
```

#### 2. In Generic Interfaces

When a class implements a generic interface, it can provide a type argument to "close" the generic or remain generic itself.

```
interface Printable<T> {
    void print(T t);
}

// 'String' is the Type Argument provided to the interface
class StringPrinter implements Printable<String> {
    @Override
    public void print(String s) { System.out.println(s); }
}
```

#### 3. In Generic Methods

When calling a generic method, the type argument is usually inferred by the compiler based on the data you pass in, but it can be specified explicitly.

```
public static <T> void show(T t) { /*...*/ }

// Explicit type argument 'Double'
ClassName.<Double>show(3.14); 

// Inferred type argument 'Integer'
show(100); 
```

---

### Constraints on Type Arguments

- **Reference Types Only:** Type arguments must be classes or interfaces. You cannot use primitives like `int` or `double`. You must use their **Wrapper Classes** (`Integer`, `Double`).
    
- **Compile-Time Verification:** Once a type argument is provided, the compiler ensures that only that specific type (or its subclasses) can be used with that instance.
    
- **Diamond Operator (`<>`):** Since Java 7, you don't need to repeat the type argument on the right side of the assignment; the compiler infers it from the left side.

---

### Why the Distinction Matters?

Understanding the difference between the **Parameter** (the blueprint) and the **Argument** (the specific material) is key to troubleshooting **Type Erasure**. At runtime, the Type Arguments are removed, and the JVM sees only the bounds or `Object`, but the compiler used those Arguments to ensure your code was safe before it ever ran.