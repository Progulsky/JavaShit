---
tags:
  - "#java"
  - "#java_core"
  - functional
---
# Method_References

**Related notes:** [[Lambda_Expression]], [[Functional_Interface]], [[Method]]

---

**Method references** are a shorthand syntax for a lambda expression that simply calls an existing method. If a lambda does nothing but pass its arguments to a method, a method reference makes the code cleaner, more readable, and more professional by removing the "middleman" of the argument list.

---

### The Four Types of Method References

Method references use the double-colon `::` operator. Here is how they map to traditional lambdas:

| **Type**                                 | **Syntax**            | **Lambda Equivalent**                | **Usage Example**     |
| ---------------------------------------- | --------------------- | ------------------------------------ | --------------------- |
| **Static Method**                        | `Class::staticMethod` | `(args) -> Class.staticMethod(args)` | `Integer::parseInt`   |
| **Instance Method (Bounded Receiver)**   | `instance::method`    | `(args) -> instance.method(args)`    | `System.out::println` |
| **Instance Method (Unbounded Receiver)** | `Class::method`       | `(obj, args) -> obj.method(args)`    | `String::toLowerCase` |
| **Constructor**                          | `Class::new`          | `(args) -> new Class(args)`          | `ArrayList::new`      |

---

### Deep Dive into the Types

#### 1. Static Method References

Used when the lambda calls a static method of a class. The arguments of the lambda are passed directly as arguments to the method. Can only be used through Type Reference

- **Example:** `List.of("1", "2").stream().map(Integer::parseInt);`

#### 2. Instance Method of a Specific Object

Used when you have an existing object (like `System.out`) and you want to call one of its methods.

- **Example:** `list.forEach(System.out::println);`

#### 3. Instance Method of an Arbitrary Object of a Particular Type

This is often the most confusing type. Here, the **first argument** of the lambda becomes the **target** of the method call, and any additional arguments are passed to the method.

- **Example:** `String::toUpperCase` is equivalent to `(String s) -> s.toUpperCase()`.

#### 4. Constructor References

Used to refer to a constructor. This is frequently used with the `Supplier` interface or factory patterns.

- **Example:** `Supplier<List<String>> listSupplier = ArrayList::new;`

---

### Why Use Them?

- **Conciseness:** They eliminate the boilerplate of naming parameters that are just being passed through.
    
- **Readability:** They allow you to refer to the method by its name, making the intent of the code immediately clear.
    
- **Maintenance:** If a method name changes, the reference is often easier to refactor than a complex lambda body.

> **AI Tip:** Use a method reference whenever a lambda is a "pass-through." If you need to perform logic _around_ the method call (like `s -> System.out.println("Value: " + s)`), you must stick with a standard lambda.