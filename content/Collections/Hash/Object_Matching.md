---
tags:
  - "#java"
  - "#java_core"
---
# Object_Matching

**Related notes:** 

---

In Java, "object matching" can refer to two distinct concepts: **comparing objects** to see if they are the same (Equality) and **checking an object's structure/type** to extract data (Pattern Matching).

---

### I. Equality Matching (Is this object the same as that one?)

This is the traditional way to check if two variables refer to the "matching" object or value.

#### 1. Reference Matching (`==`)

This checks if two variables point to the **exact same memory address**. It does not look at the data _inside_ the object.

- **Usage:** `if (objectA == objectB)`
    
- **Behavior:** Returns `true` only if both are the exact same instance on the heap.

#### 2. Logical Matching (`.equals()`)

This checks if two objects are **logically equivalent** based on their content.

- **Usage:** `if (objectA.equals(objectB))`
    
- **Behavior:** By default (in the `Object` class), this behaves like `==`. However, classes like `String`, `Integer`, `List`, and `Record` override this method to compare the actual data inside.
    
- **The Contract:** If you override `.equals()`, you strictly must override `.hashCode()`. If two objects match logically, they must produce the same hash code.

#### 3. Null-Safe Matching (`Objects.equals`)

A utility wrapper to safely match objects without risking a `NullPointerException`.

- **Usage:** `if (Objects.equals(a, b))`
    
- **Behavior:** It handles null checks for you. If `a` is null, it won't crash; it simply returns `false` (or `true` if both are null).

---

### II. Pattern Matching (Does this object fit this shape?)

It involves testing whether an object has a certain structure (like a specific class or record shape) and then **immediately extracting** its data.

#### 4. Type Pattern Matching (`instanceof`)

Historically, you had to check a type and then cast it manually. Modern Java combines these steps.

- **Old Way:**

```
    if (obj instanceof String) {
        String s = (String) obj; // Manual casting
        System.out.println(s.length());
    }
```

- **Modern Way (Java 16+):**

```
    // Checks if obj is a String AND assigns it to variable 's' if true
    if (obj instanceof String s) {
        System.out.println(s.length());
    }
```

#### 5. Switch Pattern Matching (Java 21+)

This allows you to match an object against multiple types in a clean `switch` statement, rather than using a chain of `if-else` blocks.

```
    String result = switch (obj) {
        case Integer i -> "It is an integer: " + i;
        case String s  -> "It is a string: " + s;
        case null      -> "It is null";
        default        -> "Unknown type";
    };
```

#### 6. Guarded Patterns (`when`)

Sometimes matching the type isn't enough; you need to match the type **and** a boolean condition. You can use the `when` keyword in a switch.

```
    switch (obj) {
        // Matches only if it is a String AND has length > 5
        case String s when s.length() > 5 -> System.out.println("Long string");
        case String s -> System.out.println("Short string");
        ...
    }
```

#### 7. Record Patterns (Deconstruction)

This is the most advanced form of structural matching. If you are using Java `record`s (immutable data carriers), you can match the object and "deconstruct" it into its components in one line.

- **Scenario:** You have a record `Point(int x, int y)`.

```
    if (obj instanceof Point(int x, int y)) {
        // You can access x and y directly here without calling getters
        System.out.println("X is " + x + ", Y is " + y);
    }
```

	This also works inside `switch` statements

---

### III. Functional/Stream Matching

When working with collections (Lists, Sets) in Java Streams, "matching" refers to checking if elements in a list satisfy a condition (Predicate).

- **`anyMatch(Predicate p)`:** Returns `true` if _at least one_ element matches the condition.
    
- **`allMatch(Predicate p)`:** Returns `true` if _every_ element matches.
    
- **`noneMatch(Predicate p)`:** Returns `true` if _zero_ elements match.

```
List<String> names = List.of("Alice", "Bob", "Charlie");
boolean hasBob = names.stream().anyMatch(name -> name.equals("Bob"));
```
