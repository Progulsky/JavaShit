---
tags:
  - "#java"
  - "#java_core"
  - fundamentals
  - control_flow
  - loops
---
# Do-While_Statement

**Related notes:** [[While_Statement]], [[Code_Block]], [[Scope]]

---

The `do-while` loop is similar to the `while` loop, but with one critical difference: it **executes the code block once regardless of the condition**, because the condition is evaluated **after** the block runs.

```
do {
    // code block to be executed
} while (condition);

// EXAMPLE
int i = 1;
do {
    System.out.println("i = " + i);
    i++;
} while (i <= 5);
```