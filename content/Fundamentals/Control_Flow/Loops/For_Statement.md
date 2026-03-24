---
tags:
  - "#java"
  - "#java_core"
  - fundamentals
  - control_flow
  - loops
---
# For_Statement

**Related notes:** [[For-Each_Statement]], [[Code_Block]], [[Scope]]

---

The **For loop** is best used when you know exactly how many times the code should execute.

---
### **Syntax**

```
for (initialization; condition; update) {
    // code block
}

// EXAMPLE
for (int i = 1; i <= 5; i++) {
    System.out.println("i = " + i);
}
```

- **Initialization:** Runs once before the loop starts. Used to declare and initialize loop control variables. You can declare multiple variables, but they must be of the **same data type**.
    
    - _Rule:_ Variables declared here are local to the loop and **not accessible outside** the loop block.
    
- **Condition:** An expression that is checked before every iteration to control when the loop ends.
    
- **Update:** A statement that controls how the loop variable changes after each iteration.

> **Note:** Even if you do not use certain parameters, you **must keep the semicolons** (e.g., `for (int i; ; )`).