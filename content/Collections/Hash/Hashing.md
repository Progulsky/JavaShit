---
tags:
  - "#java"
  - "#java_core"
---
# Hashing

**Related notes:** 

---

Hashing in Java is a fundamental concept used primarily to store and retrieve data quickly. At its core, it is the process of converting an object into an integer value (the **hash code**) which acts as an index to store the object in a data structure.

Here is a breakdown of how it works, the rules you must follow, and the collections that use it.

---

### 1. How Hashing Works

Imagine a massive library. Instead of searching every shelf for a book, you look up a code in a catalog that tells you exactly which aisle and shelf to check.

In Java:

- **The "Book"** is your Object (Key).
    
- **The "Code"** is the integer returned by the `hashCode()` method.
    
- **The "Shelf"** is the "bucket" in a hash-based collection (like `HashMap`).

When you save an object to a `HashMap`, Java calculates its hash code to determine where to put it. When you want to retrieve it, Java calculates the hash code again to find it instantly, rather than scanning the whole list.

---

### 2. The `hashCode()` Method

Every object in Java inherits the `hashCode()` method from the `java.lang.Object` class.

- **Default Behavior:** By default, `Object.hashCode()` typically returns an integer based on the object's memory address. This means two different objects with the exact same data will have _different_ hash codes unless you override this method.
    
- **Custom Behavior:** When you create a custom class (e.g., `Person`), you usually want equality to be based on data (like ID or email), not memory address. Therefore, you must override `hashCode()`.

---

### 3. The Golden Rule: The `equals()` and `hashCode()` Contract

This is the most critical concept in Java hashing. If you break this contract, your collections (like `HashMap` or `HashSet`) will lose data or behave unpredictably.

1. **Consistency:** If an object is not modified, `hashCode()` must return the same value every time.
    
2. **Equal Objects:** If `a.equals(b)` is true, then `a.hashCode()` **must** be equal to `b.hashCode()`.
    
3. **Unequal Objects:** If `a.equals(b)` is false, their hash codes _can_ be the same (this is called a **collision**), but distinct hash codes help performance.


> **Key Takeaway:** If you override `equals()`, you **must** override `hashCode()`.

---

### 4. Implementation Example

Here is how you typically implement this in a modern Java class using `java.util.Objects`.

```
import java.util.Objects;

public class User {
    private String email;
    private long id;

    public User(String email, long id) {
        this.email = email;
        this.id = id;
    }

    @Override
    public boolean equals(Object o) {
        // 1. Check if it's the same memory reference
        if (this == o) return true;
        // 2. Check for null and class type
        if (o == null || getClass() != o.getClass()) return false;
        // 3. Cast and compare fields
        User user = (User) o;
        return id == user.id && Objects.equals(email, user.email);
    }

    @Override
    public int hashCode() {
        // Generates a hash code based on the fields used in equals()
        return Objects.hash(email, id);
    }
}
```

---

### 5. Common Collections using Hashing

- **`HashMap`**: Stores Key-Value pairs. Uses the Key's hash code to sort data. Keys must be unique.
    
- **`HashSet`**: Stores unique objects. Internally, it actually uses a `HashMap` (where the value is just a dummy object).
    
- **`LinkedHashMap`**: Like a HashMap, but maintains the insertion order of elements.

---

### Summary Table

| **Concept**    | **Description**                                                                                                                                                          |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Speed**      | Hashing allows for $O(1)$ (constant time) average complexity for insertion and retrieval.                                                                                |
| **Collision**  | When distinct objects share a hash code. Handled via Linked Lists or Trees.                                                                                              |
| **Null Keys**  | `HashMap` allows one `null` key (hashed to bucket 0). `Hashtable` does not.                                                                                              |
| **Mutability** | **Warning:** Mutable objects make dangerous keys. If an object's fields change _after_ it is put into a Map, its hash code changes, and the Map may never find it again. |
