---
tags:
  - "#java"
  - "#java_core"
  - generic
  - type_system
---
# Wildcard

**Related notes:** [[Generic]]

---

A **Wildcard** (`?`) represents an unknown type in Java Generics. It provides a way to relax the strictness of generic types, allowing methods to operate on a broader range of related collections. Wildcards can only be used as **Type Arguments** (e.g., in variable declarations or method parameters), never in the definition of a generic class or method itself.

---

### Types of Wildcards

#### 1. Unbounded Wildcard (`?`)

This represents "any type." Use this when the code inside the method only depends on functionality provided by the `Object` class or doesn't care about the type at all.

```
public static void printList(List<?> list) {
    for (Object obj : list) {
        System.out.print(obj + " ");
    }
}
// Works for List<Integer>, List<String>, List<Dog>, etc.
```

#### 2. Upper Bounded Wildcard (`? extends Type`)

This represents "any type that is `Type` or a subtype of `Type`." It allows you to call methods defined in the bounding class.

```
public static double sumList(List<? extends Number> list) {
    double sum = 0.0;
    for (Number num : list) {
        sum += num.doubleValue(); // Safe because T is at least a Number
    }
    return sum;
}
```

#### 3. Lower Bounded Wildcard (`? super Type`)

This represents "any type that is `Type` or a supertype (parent) of `Type`." This is primarily used when you need to write data into a collection safely.

```
public static void addIntegers(List<? super Integer> list) {
    list.add(10); // Safe because the list is guaranteed to handle Integers
}
```

---

### The PECS Rule

The **PECS** rule (Producer `Extends`, Consumer `Super`) is the golden rule for deciding which wildcard to use.

| **Wildcard**        | **Perspective**         | **Guarantee**                             | **Operation**      |
| ------------------- | ----------------------- | ----------------------------------------- | ------------------ |
| **`<? extends T>`** | "Ceiling" (Upper Bound) | Everything inside is a **T**              | **Read** (Getter)  |
| **`<? super T>`**   | "Floor" (Lower Bound)   | Everything inside is **not lower than T** | **Write** (Setter) |

### 1. Producer (`? extends T`) — The Outbound Guarantee

Imagine a box labeled **"Contains some kind of Fruit."**

- **Why you can READ:** You don’t know if it’s specifically apples or bananas, but you are 100% sure it is a **Fruit**. You can safely call `.getVitaminC()` on anything you pull out.
    
- **Why you cannot WRITE:** What if the box is actually meant only for Apples, and you try to shove an Orange inside? The compiler says: "No, I won't take that risk."

### 2. Consumer (`? super T`) — The Inbound Guarantee

Imagine a storage bin certified to hold **"at least Apples."**

- **Why you can WRITE:** This bin could be designed for "Apples," "Fruits," or even "Anything" (`Object`). No matter what it is, an **Apple** will always fit (due to polymorphism).
    
- **Why you cannot READ:** If you pull something out, it could be an apple, but it could also be a piece of meat (if it’s an "Anything" bin). The only thing you know for sure about the object you retrieved is that it is an `Object`.

---

### Important Constraints

- **Single Bound:** A wildcard can have only one bound (either `super` or `extends`). You cannot write `? extends A & B`.
    
- **No Instance Creation:** You cannot instantiate an object with a wildcard (e.g., `new ArrayList<?>()` is not allowed for direct creation).