---
tags:
  - "#java"
  - "#java_core"
  - functional
  - interface
---
# Predicate

**Related notes:** [[Built-in_Functional_Interfaces]], [[Functional_Interface]]

---

In Java, a **`Predicate<T>`** is a functional interface that represents a boolean-valued function of one argument. It is part of the `java.util.function` package and is primarily used for filtering, conditional checks, or any logic that returns a **true** or **false** result.

---

### 1. The Core Contract

Since it is a **Functional Interface**, it has exactly one abstract method:

- **Method Signature**: `boolean test(T t)`
    
- **Logic**: It takes an object of type `T` and returns `true` if it matches the condition, otherwise `false`.

```
// Example: A predicate that checks if a string is longer than 5 characters
Predicate<String> isLongerThan5 = s -> s.length() > 5;

System.out.println(isLongerThan5.test("Hello"));      // false
System.out.println(isLongerThan5.test("JavaBackend")); // true
```

---

### 2. Logical Composition (Default Methods)

One of the most powerful features of `Predicate` is the ability to combine multiple conditions using default methods. This follows the rules of formal logic.

- **`.and(Predicate other)`**: Logical **AND**. Both conditions must be true.
    
- **`.or(Predicate other)`**: Logical **OR**. At least one condition must be true.
    
- **`.negate()`**: Logical **NOT**. Flips the result of the predicate.

```
Predicate<Integer> isPositive = n -> n > 0;
Predicate<Integer> isEven = n -> n % 2 == 0;

// Combine them
Predicate<Integer> isPositiveAndEven = isPositive.and(isEven);

System.out.println(isPositiveAndEven.test(4));  // true
System.out.println(isPositiveAndEven.test(-2)); // false
```

---

### 3. Static Methods

The interface also provides static helper methods:

- **`Predicate.isEqual(Object targetRef)`**: Returns a predicate that tests if two arguments are equal according to `Objects.equals(Object, Object)`.
    
- **`Predicate.not(Predicate target)`**: (Added in Java 11) A clean way to negate a predicate.
    
    - Example: `list.stream().filter(Predicate.not(String::isEmpty))...`


---

### 4. Common Use Cases

You will encounter `Predicate` most frequently in the **Stream API** and **Collections**:

1. **Filtering Streams**:

```
    List<String> names = List.of("Java", "Rust", "Python", "C");
    List<String> shortNames = names.stream()
                                   .filter(s -> s.length() < 4)
                                   .toList(); // Results in ["C"]
```

2. **Removing from Collections**:

```
    List<Integer> numbers = new ArrayList<>(List.of(1, 2, 3, 4, 5));
    numbers.removeIf(n -> n % 2 != 0); // Removes all odd numbers
```