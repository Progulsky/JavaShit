---
tags:
  - "#java"
  - "#java_core"
  - functional
  - interface
---
# Function

**Related notes:** [[Built-in_Functional_Interfaces]], [[Functional_Interface]]

---

In the `java.util.function` package, the **`Function<T, R>`** interface is perhaps the most versatile. While a `Predicate` is for logic and a `Supplier`/`Consumer` are for data boundaries, a **`Function` represents a transformation** — taking one type of data and turning it into another.

---

### 1. The Core Contract

As a **Functional Interface**, it contains exactly one abstract method:

- **Method Signature**: `R apply(T t)`
    
- **Logic**: It accepts one argument of type `T` (the input) and returns a result of type `R` (the output).

```
// Example: A function that takes a String and returns its length (Integer)
Function<String, Integer> lengthFunction = s -> s.length();

Integer result = lengthFunction.apply("Java"); // Returns 4
```

---

### 2. Functional Composition

`Function` is unique because it allows you to chain multiple transformations together into a single "pipeline."

- **`.andThen(Function after)`**: Executes the current function first, then applies the next function to the result.
    
    - Formula: $g(f(x))$
        
- **`.compose(Function before)`**: Executes the "before" function first, then applies the current function to its result.
    
    - Formula: $f(g(x))$

```
Function<String, String> upperCase = String::toUpperCase;
Function<String, String> wrapInBrackets = s -> "[" + s + "]";

// Combined: Upper case then wrap
Function<String, String> upperThenWrap = upperCase.andThen(wrapInBrackets);

System.out.println(upperThenWrap.apply("java")); // Outputs: [JAVA]
```

---

### 3. The `identity()` Method

The interface provides a static method `Function.identity()`. It returns a function that always returns its input argument.

- **Use Case**: This is incredibly useful in **Stream API** when you need to convert a list of objects into a Map where the object itself is the value.

```
Map<Integer, User> userMap = users.stream()
    .collect(Collectors.toMap(User::getId, Function.identity()));
```