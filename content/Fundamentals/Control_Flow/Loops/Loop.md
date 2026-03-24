---
tags:
  - "#java"
  - "#java_core"
  - fundamentals
  - control_flow
  - loops
---
# Loop

**Related notes:** [[For_Statement]], [[While_Statement]], [[Do-While_Statement]], [[For-Each_Statement]], [[Code_Block]], [[Scope]]

---

**Looping** is the process of executing a block of code repeatedly, either for a specific number of times or until a predefined condition is met. It utilizes the keywords `for`, `while`, and `do`.

---
### **Scope & Nesting**

- **Unique Scope:** Every loop defines a code block with its own scope. Variables declared inside a loop are not accessible once the loop finishes.
    
- **Nesting:** Loops can be nested (a loop inside another loop). Each nested loop maintains its own independent scope.

---

## Loop Control Statements

These statements allow you to alter the flow of a loop execution.

|**Statement**|**Purpose**|
|---|---|
|**`break`**|Immediately terminates the loop and moves to the next line of code after the loop.|
|**`continue`**|Skips the remaining code in the current iteration and jumps to the next cycle.|

```
// Example: break vs continue
for (int i = 0; i < 5; i++) {
    if (i == 2) continue; // Skips 2
    if (i == 4) break;    // Stops the loop at 4
    System.out.println(i); 
}
```

---

## Advanced Trick: Labels

A **Label** is an identifier followed by a colon (`labelName:`) placed before a loop. It allows `break` and `continue` to target specific loops in nested structures.

```
outerLoop:
for (int i = 1; i <= 3; i++) {
    for (int j = 1; j <= 3; j++) {
        if (i == 2 && j == 2) {
            break outerLoop; // Exits both loops entirely
        }
        System.out.println(i + " " + j);
    }
}
```

>**When to use?** Only when you need to break out of multiple levels of nested loops simultaneously to keep logic clean.