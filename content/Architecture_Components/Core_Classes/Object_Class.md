---
tags:
  - "#java"
  - "#java_core"
  - internal
  - class
---
# Object_Class

**Related notes:** [[Class]]

---

In Java, **`java.lang.Object`** is the ultimate ancestor. Every single class in the Java ecosystem—whether it's built-in like `String` or one you write yourself—implicitly inherits from the **Object** class. This makes it the root of the entire class hierarchy.

---

### Why is Object Important?

- **Universal Consistency:** It provides a set of standard behaviors that every object is guaranteed to have.
    
- **Root of Polymorphism:** Because every class "is-an" Object, you can create collections (like an `Object[]`) that can hold any type of data.
    
- **Framework Foundation:** Java's core libraries (like the Collections Framework) rely on `Object` methods to compare items, find them in memory, or print them for debugging.

---

### Most Commonly Used Methods

While `Object` has several methods, a few are essential for daily development:

#### 1. `toString()`

By default, this method returns the class name followed by the object's memory address (the "hash code"). Overriding it allows you to provide a meaningful, human-readable description of your object.

```
@Override
public String toString() {
    return "Person[name=" + name + ", age=" + age + "]";
}

Person p = new Person("Alice", 30);
System.out.println(p); // Output: Person[name=Alice, age=30]
```

#### 2. `equals(Object obj)`

The default implementation uses the **`==` operator**, which checks if two references point to the exact same spot in memory. Usually, you want to override this to compare the **actual data** inside the objects (logical equality).

#### 3. `hashCode()`

This returns an integer representation of the object's memory address. If you override `equals()`, you **must** also override `hashCode()` to ensure the object works correctly in hash-based collections like `HashMap` or `HashSet`.

---

### Summary of Other Key Methods

|**Method**|**Purpose**|
|---|---|
|**`getClass()`**|Returns the runtime class of the object (useful for reflection).|
|**`clone()`**|Creates a field-for-field copy of the object (requires the `Cloneable` interface).|
|**`wait()`, `notify()`**|Used for **Thread Synchronization** to coordinate actions between different threads.|
|**`finalize()`**|**Deprecated.** Used to perform cleanup before Garbage Collection, but now considered unreliable.|

---

### The "Default" toString() Trap

If you see an output like `User@15db9742`, it means you forgot to override the `toString()` method. Java is simply giving you the class name (`User`) and its hexadecimal hash code.