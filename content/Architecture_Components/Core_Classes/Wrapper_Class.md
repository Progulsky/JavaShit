---
tags:
  - "#java"
  - "#java_core"
  - class
  - variable
---
# Wrapper_Class

**Related notes:** [[Primitive_Data_Types]], [[Class]]

---

**Wrapper classes** provide a way to use primitive data types (like `int`, `boolean`, etc.) as objects. They are part of the `java.lang` package and are essential because many Java features — such as **Generics** and **Collections** (like `ArrayList`) — require objects and cannot work with primitives directly.

---

### The Wrapper Class Lineup

Most wrapper classes follow the naming of their primitive counterparts but start with a capital letter.

|**Primitive**|**Wrapper Class**|
|---|---|
|`byte`|`Byte`|
|`short`|`Short`|
|`int`|**`Integer`**|
|`long`|`Long`|
|`float`|`Float`|
|`double`|`Double`|
|`char`|**`Character`**|
|`boolean`|`Boolean`|

---

### Static Utility Features

Wrapper classes are more than just "boxes" for data; they provide useful constants and static methods for type conversion and metadata.

- **Constants:** `Integer.MAX_VALUE` and `Integer.MIN_VALUE` provide the range limits of the type.
    
- **Parsing:** `Integer.parseInt("123")` or `Double.parseDouble("12.5")` convert strings into usable numeric primitives.
    
- **Metadata:** `Long.SIZE` tells you how many bits (64) are used to represent the value.

---

### Boxing, Autoboxing, and Unboxing

The process of moving between a primitive and an object is called **Boxing**.

#### 1. Manual Boxing

This is the explicit conversion. While you _could_ use constructors in the past, modern Java uses static factory methods for efficiency.

```
int num = 42;
Integer boxed = Integer.valueOf(num); // Manual boxing
```

> **Note:** `Integer.valueOf()` is preferred because it caches frequently used values (typically -128 to 127), saving memory.

#### 2. Autoboxing

Java automatically handles the conversion for you to keep code clean.

```
Integer boxedNumber = 10; // Java automatically calls Integer.valueOf(10)
```

#### 3. Auto-Unboxing

The reverse happens when you assign a wrapper object back to a primitive variable or use it in an arithmetic expression.

```
Integer boxedNumber = 20;
int num = boxedNumber; // Java automatically calls boxedNumber.intValue()
```

---

### Critical Pitfalls

While convenient, wrapper classes come with risks that primitives do not:

- **The `NullPointerException` (NPE):** Primitives always have a value (like `0` or `false`). Wrapper objects can be `null`. If you try to unbox a `null` object into a primitive, the program will crash.

```
    Integer score = null;
    int currentScore = score; // Throws NullPointerException!
```

- **Performance Overhead:** In a high-frequency loop, autoboxing creates thousands of objects unnecessarily. This can trigger frequent **Garbage Collection** and slow down your application.

```
    // Slow: creating 1000 Integer objects
    Integer sum = 0;
    for (int i = 0; i < 1000; i++) {
        sum += i; // Unboxes 'sum', adds 'i', then re-boxes the result into a new object
    }
```

---

### Why Do We Need Them?

The primary reason is **Generics**. Since Generic Type Parameters must be reference types, you cannot write `ArrayList<int>`. You must use `ArrayList<Integer>`.