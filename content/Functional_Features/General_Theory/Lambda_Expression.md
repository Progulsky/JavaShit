---
tags:
  - "#java"
  - "#java_core"
  - functional
---
# Lambda_Expression

**Related notes:** [[Functional_Interface]], [[Method_References]]

---

A **Lambda expression** is an **anonymous method** — a function without a name that doesn't belong to any specific class. It provides a concise way to implement a **functional interface** (an interface with exactly one abstract method). Think of it as a way to pass behavior as if it were data.

---

### The Syntax

The syntax is designed to be as minimal as possible, consisting of three distinct parts:

1. **Argument List:** `(parameters)` — The input for the function.
    
2. **Arrow Token:** `->` — Links the parameters to the logic.
    
3. **Body:** `{ expressions; }` — The code to be executed.

**Examples:**

- `(int a, int b) -> a + b` (Binary operation)
    
- `() -> System.out.println("Hello")` (No-arg action)
    
- `s -> s.length()` (Single parameter with inferred type)

---

### Key Characteristics

- **Type Inference:** The Java compiler is smart enough to "infer" the parameter types based on the context of the functional interface. You usually don't need to write `(String s)`, just `(s)`.
    
- **Optional Parentheses:** For a single parameter (without a declared type), parentheses are optional: `name -> name.toUpperCase()`.
    
- **`var` Usage:** You can use `var` for parameters to keep things clean, but you cannot mix `var` with explicit types in the same list. **Illegal:** `(String x, var y) -> ...`
    
- **Optional Braces:** If the body is a single expression, curly braces and the `return` keyword are unnecessary. The result of the expression is automatically returned.
    
- **Variable Scoping:** Lambdas can access local variables from the surrounding code, provided those variables are **effectively final** (meaning their value never changes after initialization).

---

### Why Use Lambdas?

|**Benefit**|**Description**|
|---|---|
|**Conciseness**|Replaces the "boilerplate" of Anonymous Inner Classes with a single line of code.|
|**Readability**|Makes the intent of the code clear by focusing on the logic rather than the structure.|
|**Stream API Engine**|Lambdas are essential for modern data processing (filtering, mapping, and reducing) in Java Streams.|
|**Functional Style**|Shifts the focus from "how" to do something (imperative) to "what" needs to be done (declarative).|
