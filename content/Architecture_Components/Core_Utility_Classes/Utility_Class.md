---
tags:
  - "#java"
  - "#java_core"
  - utility
  - static
---
# Utility_Class

**Related notes:** [[Class]]

---

A **Utility Class** (or Helper Class) is a specialized class that acts as a centralized "toolbox" for your application. Instead of representing a real-world object (like a `User` or `Account`), it provides a collection of **static methods** and **constants** to perform common, repetitive tasks across various parts of your program.

---

### Key Characteristics

To ensure a utility class is used correctly and remains efficient, it follows a strict architectural pattern:

- **Stateless:** It doesn't hold data. Its methods are "pure"—the result is determined solely by the inputs you provide, not by any internal variables.
    
- **Static Members:** Since the class isn't representing an object instance, everything inside is declared `static` so you can call it directly using the class name (e.g., `Math.abs(-5)`).
    
- **Non-instantiable:** Creating an object of a utility class is a waste of memory. To prevent this, you define a **private constructor**.
    
- **Final:** Typically marked as `final` to prevent other classes from inheriting from it, as utility classes are meant to be standalone containers.

---

### Anatomy of a Perfect Utility Class

Here is how you properly structure a utility class to follow Java best practices:

```
public final class MathUtils {

    // 1. Private constructor: Prevents anyone from using 'new MathUtils()'
    private MathUtils() {
        // Optional: Throw exception to prevent instantiation even via Reflection
        throw new UnsupportedOperationException("Utility class");
    }

    // 2. Static constant: A shared value accessible everywhere
    public static final double PI_APPROX = 3.14159;

    // 3. Static helper methods: Logic that doesn't need object state
    public static int square(int number) {
        return number * number;
    }

    public static boolean isEven(int number) {
        return number % 2 == 0;
    }
}

// Usage:
int result = MathUtils.square(4); // No 'new' keyword needed
```

---

### Famous Examples in Java

You’ve likely already used several built-in utility classes provided by the Java Standard Library:

|**Class**|**Purpose**|
|---|---|
|**`java.lang.Math`**|Mathematical functions like `sqrt()`, `pow()`, and `random()`.|
|**`java.util.Arrays`**|Tools for sorting, searching, and printing arrays.|
|**`java.util.Collections`**|Logic for manipulating lists, sets, and maps.|
|**`java.util.Objects`**|Null-safe methods for comparing or hashing objects.|

---

### Why Use Them?

- **Don't Repeat Yourself (DRY):** Instead of writing a "capitalize string" method in five different classes, you write it once in a `StringUtils` class.
    
- **Namespace Organization:** Groups related logic together, making your project structure easier to navigate.
    
- **Global Access:** Since the methods are static, they are available to any class in your project without the overhead of passing objects around.

> **Peer Tip:** While utility classes are great, don't overdo it. If you find yourself putting _everything_ into utility classes, you might be moving away from **Object-Oriented Programming** and back toward **Procedural Programming**. Use them only for truly generic, shared logic.