---
tags:
  - "#java"
  - "#java_core"
  - fundamentals
  - control_flow
  - conditional_logic
---
# Switch

**Related notes:** [[Conditional Logic]], [[Code_Block]], [[Scope]]

---

A **switch statement** tests a single variable against a list of constant values called **cases**.

---

## 1. Basic Rules

- **Cases:** Each value represents a potential match. Can stack several cases to one block
    
- **Default:** Executes if no match is found (similar to `else`). 
    
- **Break:** Prevents "fall-through" (where the code continues into the next case regardless of a match).
    
- **Compatible Types:** Switches are limited to `byte`, `short`, `int`, `char`, `String`, `enum`, and their respective Wrapper Classes.

---

## 2. Switch with Return Keyword

If a switch is inside a method, you can use the `return` keyword directly within the cases.

```
public String getDayName(int day) {
    switch (day) {
        case 1: return "Monday";
        case 2: return "Tuesday";
        default: return "Unknown";
    }
}
```

> [!IMPORTANT] The default keyword is essential when switch are part of expression or return a value

---

## 3. Comparison: Old vs. New Switch

|**Feature**|**Old Switch (Statement)**|**New Switch (Expression)**|
|---|---|---|
|**Syntax**|Uses `:` and `break`.|Uses `->` (Arrow syntax).|
|**Scope**|All cases share the same scope.|Each case has a **unique scope**.|
|**Return**|Cannot directly return a value.|Can be assigned to a variable or returned.|
|**Yield**|Not available.|Uses `yield` for multi-line blocks.|

### Old Switch Example

```
switch (variable) {
    case value1:
        // code block
        break;
    case value2: case value3: case value52: // several cases to 
        // another code block                   one code block
        break;
    default:
        // code if no cases match
}
```

### New Switch Example (JDK 12+)

In the new version, `break` is not needed. If a case has multiple statements, you must use a code block `{}` and the `yield` keyword to return the value.

```
int day = 2;  
String dayName = switch (day) {  
    case 1 -> "Monday";  
    case 2, 3, 4 -> {
        System.out.print("Happy ");  
        yield "Tuesday"; // Returns value to the variable
    }  
    default -> "Invalid day";  
};  
```

> [!IMPORTANT] The return type of a switch expression must match the type of the variable it is being assigned to.
