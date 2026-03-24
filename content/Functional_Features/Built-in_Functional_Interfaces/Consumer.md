---
tags:
  - "#java"
  - "#java_core"
  - functional
  - interface
---
# Consumer

**Related notes:** [[Built-in_Functional_Interfaces]], [[Functional_Interface]]

---

In Java's functional programming world, a **Consumer** is a functional interface that represents an operation that **accepts a single input argument and returns no result**. Think of it as a "one-way street": data goes in, an action is performed, and nothing comes back (it has a `void` return type).

### 1. The Core Definition

Located in the `java.util.function` package, its structure is straightforward:

```
@FunctionalInterface
public interface Consumer<T> {
    void accept(T t);
}
```

- **`T`**: The type of the input to the operation.
    
- **`accept(T t)`**: The single abstract method (SAM) used to perform the operation on the given argument.

---

### 2. Common Use Cases

Consumers are most frequently used in situations where you want to perform an action for every element in a collection, such as printing, saving to a database, or updating a UI.

```
List<String> names = List.of("Alice", "Bob", "Charlie");

// Using a lambda expression as a Consumer
names.forEach(name -> System.out.println("Hello, " + name));

// Using a method reference as a Consumer
names.forEach(System.out::println);
```

---

### 3. Chaining Consumers with `andThen()`

One of the powerful features of the `Consumer` interface is the default method `andThen(Consumer<? super T> after)`. This allows you to compose multiple consumers to run sequentially on the same input.

```
Consumer<String> upperCasePrint = s -> System.out.println(s.toUpperCase());
Consumer<String> lowerCasePrint = s -> System.out.println(s.toLowerCase());

// 'combined' will run upperCasePrint first, then lowerCasePrint
Consumer<String> combined = upperCasePrint.andThen(lowerCasePrint);

combined.accept("Java Language"); 
// Output:
// JAVA LANGUAGE
// java language
```

