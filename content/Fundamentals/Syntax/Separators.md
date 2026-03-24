---
tags:
  - "#java"
  - "#java_core"
  - fundamentals
  - syntax
---
# Separators

**Related notes:** [[Token]]

---

In Java, **separators** (also known as punctuators) are tokens that do not perform operations but are used to define the structure and organization of the code. They help the compiler understand where elements start, end, and how they are grouped.

---

### Common Separators in Java

|**Symbol**|**Name**|**Usage & Purpose**|
|---|---|---|
|**`;`**|**Semicolon**|Ends a statement. Every complete instruction (like a variable declaration or assignment) must end with this.|
|**`{ }`**|**Curly Braces**|Defines a **Code Block**. Used for classes, methods, and control flow (like `if` statements and loops).|
|**`( )`**|**Parentheses**|Used in **method declarations** to hold parameters, in **method calls** for arguments, and to control **expression priority**.|
|**`[ ]`**|**Brackets**|Used for **array declarations** and to access specific elements within an array.|
|**`,`**|**Comma**|Separates individual identifiers in a **variable declaration** or multiple arguments in a method call.|
|**`.`**|**Period (Dot)**|Used to separate package names from sub-packages and classes, or to access **methods and variables** of an object.|
|**`...`**|**Ellipsis**|Used in method declarations for **variable-length argument lists** (varargs).|
|**`::`**|**Double Colon**|Used for **method references** (introduced in Java 8).|
|**`@`**|**At Sign**|Used to begin **annotations**.|

---

### Examples in Code

```
// Parentheses used for method parameters; Curly braces for the method block
void myMethod(int a, int b) { 
    
    // Brackets for array; Semicolon to end the statement
    int[] numbers = {a, b}; 
    
    // Dot to access the println method; Comma to separate items
    System.out.println("Values: " + a + ", " + b); 
}
```
