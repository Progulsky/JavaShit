---
tags:
  - "#java"
  - "#java_core"
  - fundamentals
  - metadata
---
# Modifier

**Related notes:** [[Keyword]], [[Class]], [[Method]], [[Variable]]

---

**Modifiers** are keywords that change the behavior of **Classes**, **Methods**, and **Variables**. They instruct the compiler and **JVM** on how an element should be used, defining its visibility, behavior, and restrictions.

---

## Access Modifiers

These modifiers determine the visibility and who can access a specific class, method, or variable.

|**Modifier**|**Description**|**Applicable to**|
|---|---|---|
|**`public`**|Accessible from **anywhere** in the program (any package).|Class, Method, Variable, Constructor|
|**`protected`**|Accessible within the **same package** and by **subclasses** in other packages.|Method, Variable, Constructor|
|**`default`** (Nothing)|**Package access**: Accessible only to elements within the **same package**.|Class, Method, Variable, Constructor|
|**`private`**|Accessible **only within the same class**. No other element has access.|Method, Variable, Constructor|

---

## Non-Access Modifiers

These define specific properties and behaviors rather than visibility.

#### **1. Class-level Non-Access Modifiers**

- **`final`**: The class cannot be extended (prevents subclassing).
    
- **`abstract`**: The class cannot be instantiated and may contain abstract methods.
    
- **`static`**: Used for nested classes; belongs to the outer class rather than an object instance.

#### **2. Method-level Non-Access Modifiers**

- **`final`**: The method cannot be overridden by subclasses.
    
- **`abstract`**: The method has no body and must be implemented by a subclass.
    
- **`static`**: The method belongs to the class itself and can be called without creating an object.
    
- **`synchronized`**: Restricts access so only one thread can execute the method at a time.
    
- **`native`**: Indicates the method is implemented in another language (like C/C++).
    
- **`strictfp`**: Ensures floating-point calculations are consistent across different platforms.
    
- **`default`**: Used within an interface to provide a method with a body.

#### **3. Variable-level Non-Access Modifiers**

- **`final`**: The value cannot be changed once initialized (creates a constant).
    
- **`static`**: The variable belongs to the class and is shared among all instances/objects.
    
- **`transient`**: The variable is skipped during the serialization process.
    
- **`volatile`**: Ensures the variable's value is always read from the main memory, not from a thread's local cache.