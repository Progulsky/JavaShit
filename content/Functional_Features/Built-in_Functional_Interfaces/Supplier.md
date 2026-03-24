---
tags:
  - "#java"
  - "#java_core"
  - functional
  - interface
---
# Supplier

**Related notes:** [[Built-in_Functional_Interfaces]], [[Functional_Interface]]

---

In the world of Java Functional Interfaces, **`Supplier<T>`** is the opposite of a `Consumer`. While a Consumer takes an object and returns nothing, a **Supplier takes nothing and returns an object**.

It is part of the `java.util.function` package and represents a function that "supplies" a result.

---

### 1. The Core Contract

As a **Functional Interface**, it contains exactly one abstract method:

- **Method Signature**: `T get()`
    
- **Logic**: It takes no arguments and returns a result of type `T`.

```
// Example: A supplier that provides a current timestamp string
Supplier<LocalDateTime> nowSupplier = LocalDateTime::now;

LocalDateTime currentTime = nowSupplier.get();
System.out.println("Current time: " + currentTime);
```

---

### 2. Why use a Supplier? (The Power of Laziness)

The primary reason to use a `Supplier` instead of a direct value is **Lazy Evaluation**. The code inside the supplier only runs when you call `.get()`, not when you define the supplier.

#### A. Performance Optimization in Logging

Instead of constructing a heavy string every time, you can supply it only if the log level is actually enabled.

```
// String is constructed only if logger needs it
logger.info(() -> "Expensive report data: " + fetchComplexData()); 
```

#### B. Working with `Optional`

This is one of the most common places you'll see a Supplier in backend code.

```
// .orElse() always creates the object, even if the Optional is not empty.
// .orElseGet() takes a Supplier and only creates the object if the Optional is empty.
User user = userRepository.findById(id)
                          .orElseGet(() -> new User("Anonymous")); 
```

---

### 3. Method References and Factories

Suppliers are often used as **factories**. Any constructor that takes no arguments can be treated as a `Supplier`.

- `Supplier<List<String>> listSupplier = ArrayList::new;`
    
- `Supplier<MyNode> nodeSupplier = MyNode::new;`
