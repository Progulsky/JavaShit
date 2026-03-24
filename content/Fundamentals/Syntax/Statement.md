---
tags:
  - "#java"
  - "#java_core"
  - fundamentals
  - syntax
  - variable
---
# Statement

**Related notes:** [[Code_Block]], [[Expression]], [[Variable]]

---

A **statement** is a complete instruction that the Java compiler can execute. Statements typically end with a **semicolon (`;`)** and may include one or more **expressions**.

You can write multiple statements on a single line by separating them with semicolons:

`short var1 = 45; long var2 = 3000`

---

### Examples of Statements

|**Statement**|**Purpose**|
|---|---|
|`System.out.print("Hello World");`|Method invocation statement|
|`int x = 10;`|Declaration and initialization statement|
|`count++;`|Increment (expression) statement|

---

### Types of Statements

Java statements can be categorized based on their function:

- **Declaration Statement**: Used to define a **variable** by specifying its data type and name. You can declare multiple variables on one line using a comma, provided they share the same data type.
    
    - _Example:_ `byte var1, var2`
    
- **Initialization Statement**: Used to assign a value to a variable. This can be done separately or during the declaration.
    
    - _Example:_ `byte var1 = 1, var2 = 2`
    
- **Redeclaration Statement**: An attempt to change a variable's value by using a **keyword** again (e.g., `int var = 5; int var = 10`).
    
    - > **Note:** Redeclaration is not allowed in IDEs and will result in an error, though it is permitted in **jShell**.
    
- **Reassignment**: Changing the value of an existing variable without using a keyword.
    
    - _Example:_ `int var = 5; var = 10`
