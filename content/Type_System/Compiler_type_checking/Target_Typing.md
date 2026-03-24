---
tags:
  - "#java"
  - "#java_core"
  - type_system
---
# Target_Typing

**Related notes:** [[Type_Inference]], [[Type_Witness]]

---

**Target Typing** is a sophisticated form of **Type Inference** where the Java compiler identifies the type of an expression based on its **destination**. Instead of analyzing an expression in isolation (bottom-up), the compiler looks "top-down" at where the result is being assigned, passed, or returned to determine what the type should be.

---

### Core Concept: Context Matters

In many programming scenarios, a single expression could technically represent multiple different types. The "Target Type" is the data type that the context expects.

- **The Expression:** `() -> System.out.println("Hello")`
    
- **The Target:** If assigned to a `Runnable`, the target type is `Runnable`. If passed to a method expecting a `Consumer<String>`, the target type is `Consumer<String>`.

---

### Key Contexts for Target Typing

#### 1. Variable Assignment

The type on the left side of the `=` operator dictates the type of the expression on the right. This is the foundation for using Lambdas.

```
// Target is Runnable; Lambda is inferred as a Runnable implementation
Runnable r = () -> System.out.println("Running..."); 
```

#### 2. Method Arguments

When you pass a Lambda or a generic method result into a method, the compiler looks at the method's signature to find the target.

```
List<String> names = Arrays.asList("Alice", "Bob");

// Target type for 's -> ...' is Consumer<String>, defined by the forEach method
names.forEach(s -> System.out.println(s)); 
```

#### 3. Return Statements

If a method is defined to return a specific functional interface, the compiler uses that return type as the target for the expression inside the method.

```
public Function<String, Integer> getLengthMapper() {
    // Target type is Function<String, Integer>
    return s -> s.length(); 
}
```

---

### Evolution: Generalized Target Typing

Java's ability to infer types from targets has expanded significantly over time to make code cleaner and more intuitive.

#### Java 7 and the Diamond Operator

Java 7 introduced the ability for the target (the variable declaration) to inform the instantiation of a generic class.

```
// Target is List<String>, so <> is inferred as <String>
List<String> list = new ArrayList<>(); 
```

#### Java 8 and Nested Contexts

Before Java 8, target typing was often limited to direct assignments. Java 8 introduced **Generalized Target Typing**, allowing the compiler to look through nested method calls to find the target.

|**Version**|**Example**|**Status**|
|---|---|---|
|**Java 7**|`process(Collections.<String>emptyList())`|**Manual:** Required explicit type witness inside arguments.|
|**Java 8+**|`process(Collections.emptyList())`|**Automatic:** Compiler looks at `process` parameters to infer `emptyList`.|

---

### Why Target Typing is Valuable

- **Conciseness:** You don't have to repeat type information (like `<String>`) throughout your code.
    
- **Lambda Support:** Target typing is what makes Lambdas possible; without it, you would have to explicitly cast every Lambda to its functional interface.
    
- **Readable API Design:** Allows library creators to build "fluent" APIs that feel natural to use because the compiler handles the heavy lifting of type management.