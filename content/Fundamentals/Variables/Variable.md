---
tags:
  - "#java"
  - "#java_core"
  - fundamentals
  - variable
---
# Variable

**Related notes:** [[Statement]], [[Expression]], [[Scope]], [[Field]]

---

A **variable** is a named location in memory used to store data that can be read or modified during program execution. It serves as a fundamental building block in both **statements** and **expressions**.

When you assign one variable to another, you are **copying the value**, not creating a permanent link.

> **Example:**
> 
> If `var1 = 5` and you set `var2 = var1`, then update `var1 = 10`, `var2` remains `5`.

---

### Variable Classification (By Scope)

Java variables are categorized based on where they are declared, which determines their lifetime and visibility.

|**Type**|**Location**|**Lifetime**|**Default Value**|
|---|---|---|---|
|**Local Variables**|Inside a method or block `{}`|While the block is executing|**None** (Must be initialized)|
|**Instance Variables** (Fields)|Inside a class, outside methods|While the object exists in memory|**Yes** (0, false, or null)|
|**Static Variables**|Inside a class with `static` keyword|While the program is running|**Yes** (0, false, or null)|

---

### Key Behaviors

#### 1. The Shadowing Rule

In Java, you cannot declare a local variable with the same name as another local variable in a nested scope. However, a local variable **can** have the same name as a **class field**. This is called "shadowing." To access the shadowed field, you use the `this` keyword.

```
public class Player {
    int health = 100; // Class Field

    void heal(int health) { // Parameter shadows the field
        this.health = health; // 'this.health' refers to the field; 'health' refers to the parameter
    }
}
```
