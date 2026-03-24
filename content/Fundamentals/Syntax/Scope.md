---
tags:
  - "#java"
  - "#java_core"
  - fundamentals
  - syntax
  - variable
---
# Scope

**Related notes:** [[Code_Block]], [[Method]], [[Class]], [[Conditional Logic]], [[Loop]], [[Variable]], [[Field]], [[Exception]]

---

A **scope** is the specific region of a program where a **variable** is declared, exists in memory, and can be accessed or modified.

---

### Types of Scope

Java utilizes several levels of scope to manage variable visibility:

|**Scope Type**|**Description**|
|---|---|
|**Block Scope**|Applies to variables declared inside **code blocks** (within curly braces `{}`). These are only visible within that specific block.|
|**Method Scope**|Applies to variables declared inside a **method**. These variables exist only while the method is executing.|
|**Class Scope**|Includes **instance** or **static variables** declared inside a class but outside any method. They are accessible to all methods within that class.|

---

### Scope Hierarchy and Visibility

Each block defines its own scope. A fundamental rule of visibility is that **inner scopes can access variables from outer scopes, but outer scopes cannot access variables declared within inner ones.**

### **Examples**

**Block Scope:**
```
if (true) {
    int x = 10;
    System.out.println(x); // x is visible here
}
// System.out.println(x); // Error: x cannot be resolved
```

**Method Scope:**
```
void myMethod() {
    int a = 5;
    System.out.println(a); // a is visible here
}
// System.out.println(a); // Error: a is not visible here
```

**Class Scope:**
```
public class Example {
    int number = 42; // Instance variable

    void showNumber() {
        System.out.println(number); // Accessible here
    }
}
```

**Nested Scope Interaction:**
```
public class ScopeExample {
    public static void main(String[] args) {
        int outer = 10;

        if (outer > 5) {
            int inner = 20;
            System.out.println("Outer: " + outer); // Allowed (Outer is visible)
            System.out.println("Inner: " + inner); // Allowed
        }

        System.out.println("Outer: " + outer); // Allowed
        // System.out.println("Inner: " + inner); // Error: inner not visible here
    }
}
```