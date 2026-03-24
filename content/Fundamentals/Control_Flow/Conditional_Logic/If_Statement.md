---
tags:
  - "#java"
  - "#java_core"
  - fundamentals
  - control_flow
  - conditional_logic
---
# If_Statement

**Related notes:** [[Conditional Logic]], [[Code_Block]], [[Scope]]

---

The **If-statement** checks one or several logical operations and, based on the result, decides whether to execute a block of code.

---

## 1. Core Components

- **If-statement:** Uses logical keywords (`True`/`False`) and creates a **Code Block** with its own **Scope**.
    
- **Else-If-statement:** Chains multiple conditions. The compiler reads them from top to bottom; as soon as one matches, its block runs and the rest are skipped.
    
- **Else-statement:** The "fallback" block that executes only if no preceding `if` or `else-if` criteria were met.

> [!NOTE] `Else` and `Else-If` cannot exist without an initial `If` statement.

---

## 2. Logical Syntax Tips

- Instead of `if (varName == true)`, you can simply write `if (varName)`.
    
- Instead of `if (varName == false)`, you can write `if (!varName)`.
    
- Use extra parentheses `( (condition1) && (condition2) )` to make complex logic easier to read.


```
boolean isHasFace = false;
boolean isHasHead = true;

if (isHasFace) {
    System.out.print("Woowie");
} else if (isHasHead) {
    System.out.print("At least...");
} else {
    System.out.print("Oops");
}
```