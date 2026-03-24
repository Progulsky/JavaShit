---
tags:
  - "#java"
  - "#java_core"
  - functional
  - interface
---
# Built-in_Functional_Interfaces

**Related notes:** [[Functional_Interface]], [[Consumer]], [[Supplier]], [[Predicate]], [[Function]]

---

Java's `java.util.function` package provides a rich set of built-in functional interfaces designed to handle the most common programming tasks. These interfaces allow you to pass behavior as data, making your code more expressive and concise.

---

### The Four Pillars of Functional Interfaces

These four interfaces form the foundation of functional programming in Java:

|**Interface**|**Abstract Method**|**Semantic Role**|
|---|---|---|
|**`Predicate<T>`**|`boolean test(T t)`|**Filter:** Checks if a condition is met.|
|**`Function<T, R>`**|`R apply(T t)`|**Transform:** Converts one type to another.|
|**`Consumer<T>`**|`void accept(T t)`|**Action:** Uses an object (e.g., printing, saving).|
|**`Supplier<T>`**|`T get()`|**Factory:** Provides/creates a new object.|

---

### Expanding the Toolkit

#### 1. Increasing Arity (The "Bi-" Interfaces)

When a single argument isn't enough, Java provides interfaces that accept **two** arguments.

- **`BiPredicate<T, U>`**: e.g., checking if a user has a specific permission.
    
- **`BiConsumer<T, U>`**: e.g., processing key-value pairs in a Map.
    
- **`BiFunction<T, U, R>`**: e.g., combining two strings into a formatted result.

#### 2. Specialized Operators

Operators are simplified versions of `Function` where all types are identical.

- **`UnaryOperator<T>`**: `T -> T`. (e.g., transforming a string to lowercase).
    
- **`BinaryOperator<T>`**: `(T, T) -> T`. (e.g., finding the maximum of two numbers).

#### 3. Primitive Specializations

To avoid the performance cost of **autoboxing** (converting `int` to `Integer`), Java provides specialized versions for `int`, `long`, and `double`.

- **Standard:** `IntPredicate`, `DoubleConsumer`, `LongSupplier`.
    
- **Conversions:** `ToIntFunction<T>` (Object to `int`), `IntToDoubleFunction` (`int` to `double`).


