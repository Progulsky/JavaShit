---
tags:
  - "#java"
  - "#java_core"
  - generic
---
# Generic

**Related notes:** [[Generalization]], [[Generic_Class]], [[Generic_Method]], [[Type_Parameter]], [[Type_Argument]], [[Wildcard]], [[Type_Erasure]], [[Type_Witness]]

---

**Generics** are a powerful feature introduced to ensure **type safety** and **reusability** by allowing classes, interfaces, and methods to operate on objects of various types while providing compile-time type checking.

Before Generics (pre-Java 5), collections used the `Object` class to store data, which required manual casting and often led to the dreaded `ClassCastException` at runtime. Generics shifted this responsibility to the compiler.

---

### Core Advantages

#### 1. Type Safety

The compiler acts as a gatekeeper. If you declare a list to hold only `String` objects, the compiler will block any attempt to add an `Integer` or any other type. This prevents errors from "leaking" into the runtime phase of your program.

```
List<String> list = new ArrayList<>();
list.add("Java");
// list.add(10); // COMPILE-TIME ERROR: Prevents crashes before they happen
```

#### 2. Elimination of Casting

Without generics, every time you retrieved an item from a collection, you had to tell Java what it was. With generics, the "cast" is handled automatically behind the scenes.

```
// Without Generics (Old Way)
String s = (String) list.get(0); 

// With Generics (Modern Way)
String s = list.get(0); // No explicit cast needed
```

#### 3. Code Reusability

You can write one implementation of a data structure (like `ArrayList<T>`) and use it for `Integer`, `String`, or `Employee` objects without rewriting a single line of the internal logic.
