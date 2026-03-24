---
tags:
  - "#java"
  - "#java_core"
  - fundamentals
  - control_flow
  - loops
---
# While_Statement

**Related notes:** [[Do-While_Statement]], [[Code_Block]], [[Scope]]

---

The `while` loop repeatedly executes code as long as a specified condition is true. It is typically used when you **do not know in advance** how many times the loop should run.

**Logic:** It has only one parameter (the condition). The condition is checked **before** each iteration.

```
while (condition) {
    // code block to be executed
}

// EXAMPLE
int i = 1;
while (i <= 5) {
    System.out.println("i = " + i);
    i++;
}
```

