---
tags:
  - "#java"
  - "#java_core"
  - fundamentals
  - control_flow
  - conditional_logic
---
# Conditional Logic

**Related notes:** [[If_Statement]], [[Switch]], [[Operator]], [[Code_Block]], [[Scope]]

---

Conditional logic consists of the mechanisms used to evaluate values before executing code. It determines the flow of a program based on logical or arithmetical results.

---

## 1. Short-Circuit vs. Bitwise Operators

Programming languages (like Java) often use **short-circuit operators** to optimize performance and prevent errors.

- **Logical AND (`&&`) / Logical OR (`||`):** These skip the evaluation of the second condition if the first one already determines the outcome.
    
    - _Example:_ `if (user != null && user.isActive())`. If `user` is `null`, `isActive()` is never called, avoiding a potential crash.
        
- **Bitwise AND (`&`) / Bitwise OR (`|`):** Both conditions are **always** evaluated, even if the result is already certain after the first check.

---

## 2. The Ternary Operator

A shorthand, inline version of an `if-else` statement used for simple conditional assignments.

**Structure:** `operand1 ? operand2 : operand3`

- If `operand1` is **True**, it returns `operand2`.
    
- If `operand1` is **False**, it returns `operand3`.

```
int var1 = 10;
String var2 = "Bigger";
String var3 = "Smaller";

// Result assigned to var4
String var4 = (var1 > 1) ? var2 : var3; 
```

> [!IMPORTANT] When assigning the result to a variable, the data types must be compatible.