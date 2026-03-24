---
tags:
  - "#java"
  - "#java_core"
  - generic
  - class_member
  - method
---
# Generic_Method

**Related notes:** [[Method]], [[Generic]], [[Type_Parameter]], [[Type_Argument]], [[Wildcard]], [[Type_Inference]], [[Target_Typing]]

---

A **Generic Method** is a method that introduces its own **Type Parameters**. This allows the method to be used with different data types while maintaining compile-time type safety. Unlike generic classes, where the type is defined at the class level, a generic method defines its type locally.

---

### Implementation & Syntax

The type parameter (e.g., `<T>`) must be placed inside angle brackets **before the return type** of the method.

```
public class GenericMethodExample {
    // <T> defines the type parameter for this specific method
    public static <T> void printArray(T[] array) {
        for (T element : array) {
            System.out.print(element + " ");
        }
    }
}

// Usage: The same method handles Integers and Strings
Integer[] intArray = {1, 2, 3};
String[] stringArray = {"Java", "Generics"};

printArray(intArray);
printArray(stringArray);
```

---
### Generic Return Types

Generic methods can also return the generic type `T`. This is particularly useful for utility methods that extract data from structures.

```
public static <T> T getFirst(T[] array) {
    return (array == null || array.length == 0) ? null : array[0];
}
```

---

### Bounded Generic Methods

You can restrict the types a method accepts using the `extends` keyword. This is known as an **Upper Bound**. It ensures that the provided type is either a specific class or one of its subclasses.

```
// Restricts T to be a Number or its subclasses (Integer, Double, etc.)
public static <T extends Number> double sum(T a, T b) {
    return a.doubleValue() + b.doubleValue();
}
```

---

### Static Methods and Generics

A common point of confusion is how `static` methods interact with generic classes. Because a static method belongs to the class itself rather than a specific instance, it **cannot** access the type parameter defined at the class level.

|**Scenario**|**Code**|**Result**|
|---|---|---|
|**Invalid**|`public static void doWork(T item)`|**Compile Error:** Static context cannot reference class-level `T`.|
|**Valid**|`public static <T> void doWork(T item)`|**Success:** The method defines its own independent `T`.|

> **Key Rule:** If you want a static method to be generic, you must declare the type parameter (like `<T>`) within the method signature itself, even if the class is already generic.

---

### Why Use Generic Methods?

- **Type Safety:** Eliminates the need for manual casting and prevents `ClassCastException` at runtime.
    
- **Granular Scope:** Allows a specific method to be generic even if the rest of the class is not.
    
- **Code Reduction:** Prevents the "copy-paste" of logic for different data types.