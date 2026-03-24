---
tags:
  - "#java"
  - "#java_core"
  - type_system
  - generic
---
# Type_Erasure

**Related notes:** [[Generic]], [[Type_Parameter]], [[Type_Argument]]

---

**Type Erasure** is a core process enforced by the Java compiler to ensure that **Generics** do not incur performance overhead at runtime and remain backward compatible with older versions of Java (pre-Java 5).

Essentially, the compiler "erases" all information related to generic type parameters during compilation and replaces them with standard classes or interfaces. By the time the code reaches the **JVM**, the generics are gone.

---

### How Type Erasure Works

The compiler follows three primary steps to clean up generic code:

1. **Replaces Type Parameters:** The compiler replaces all type parameters (`<T>`) with their **first bound**. If the type is unbounded (e.g., `<T>`), it is replaced by `Object`. If it is bounded (e.g., `<T extends Number>`), it is replaced by the bound (`Number`).
    
2. **Inserts Type Casts:** Since the internal data is now stored as the bound (or `Object`), the compiler automatically inserts the necessary **Casts** to ensure your code receives the specific type you declared.
    
3. **Generates Bridge Methods:** To preserve polymorphism in extended generic types, the compiler sometimes creates "bridge methods" behind the scenes.

---

### Implementation Example

Observe how the compiler transforms your "Type Safe" code into "Legacy Compatible" bytecode.

#### Before Compilation (Your Source Code)

```
public class NumericBox<T extends Number> {
    private T value;

    public void set(T value) { 
        this.value = value; 
    }

    public T get() {
        return value;
    }
}
```

#### After Compilation (The Bytecode/JVM view)

```
public class NumericBox {
    private Number value; // T replaced by Number (the upper bound)

    public void set(Number value) { 
        this.value = value; 
    }

    public Number get() {
        return value;
    }
}
```

---

### Consequences of Type Erasure

Because the generic information is removed at runtime, there are several strict limitations you must keep in mind:

- **No Instance Creation:** You cannot do `new T()`. Since `T` is erased, the JVM wouldn't know which constructor to call.
    
- **No Primitive Types:** You cannot use `List<int>`. Because `int` is not an `Object` or a reference type, it cannot survive erasure to `Object`.
    
- **No `instanceof` with Generics:** You cannot check `if (list instanceof ArrayList<String>)`. At runtime, the JVM only knows it is an `ArrayList`; the `<String>` part is invisible.
    
- **Type Identity:** `List<String>` and `List<Integer>` are exactly the same class at runtime.

---

### Why Do This? (The "Peer" Perspective)

It might seem annoying that Java "throws away" your carefully defined types, but this design was a stroke of genius for its time. It allowed Java to add Generics in 2004 without requiring developers to rewrite billions of lines of existing code. It’s why you can still pass a modern `ArrayList<String>` to a legacy method that only expects a raw `List`.