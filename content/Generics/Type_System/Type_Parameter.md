---
tags:
  - "#java"
  - "#java_core"
  - generic
  - type_system
---
# Type_Parameter

**Related notes:** [[Generic]], [[Type_Argument]]

---

A **Type Parameter** is a formal placeholder (a label) for a type that you define inside angle brackets (`< >`). It serves as a "template" variable that represents a real class or interface to be specified later. This allows you to write reusable code that handles different data types without losing **Compile-time type safety**.

---

### Raw Types: The "Old Way"

A **Raw Type** is the name of a generic class or interface used without any type arguments. For example, using `ArrayList` instead of `ArrayList<String>`.

#### Why They Still Exist

Raw types were kept in Java to ensure **Backward Compatibility**. When Generics were introduced in Java 5, millions of lines of legacy code already existed that used "raw" collections. To prevent that code from breaking, the JVM still allows them.

#### The Dangers of Raw Types

When you use a raw type, you are effectively opting out of everything Generics provide.

| **Feature**       | **Generic Type (List<String>)**      | **Raw Type (List)**                 |
| ----------------- | ------------------------------------ | ----------------------------------- |
| **Type Checking** | Enforced by compiler                 | **None** (treated as `Object`)      |
| **Safety**        | High (prevents `ClassCastException`) | **Low** (errors happen at runtime)  |
| **Casting**       | Automatic                            | **Manual** (required for retrieval) |

```
// RAW TYPE EXAMPLE (Bad Practice)
List rawList = new ArrayList();
rawList.add("Hello");
rawList.add(100); // No error from compiler!

String s = (String) rawList.get(1); // RUNTIME ERROR: ClassCastException
```

> **Direct Peer Advice:** Always avoid raw types in modern Java. If you truly don't know what type a list will hold, it is better to use a wildcard like `List<?>` than to use a raw `List`.