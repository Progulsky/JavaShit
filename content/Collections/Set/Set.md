---
tags:
  - "#java"
  - "#java_core"
---
# Set

**Related notes:** 

---

The **`Set` interface** in Java is a core part of the Java Collections Framework (located in the `java.util` package). It extends the `Collection` interface and models the mathematical set abstraction. The defining characteristic of a `Set` is that **it cannot contain duplicate elements**.

---

### Key Characteristics of a Set

- **No Duplicates:** If you try to add an element that is already present in the set (determined by the `equals()` method), the `add()` method will simply return `false` and the set will remain unchanged.
    
- **Null Values:** Most implementations allow at most one `null` element, though some (like `TreeSet`) do not allow `null` values at all.
    
- **No Indexing:** Unlike a `List`, a standard `Set` does not provide an index-based way to access elements (e.g., there is no `get(index)` method). You must iterate through it or use methods like `contains()`.

---

### Common Implementations

| **Set Implementation** | **Best Used For**                                                     | **Ordering**       | **Time Complexity (Search/Add)**      | **Time Complexity (Add/Remove)** |
| ---------------------- | --------------------------------------------------------------------- | ------------------ | ------------------------------------- | -------------------------------- |
| **`HashSet`**          | General-purpose uniqueness where order doesn't matter. Maximum speed. | None               | `O(1)`                                | $O(1)$                           |
| **`LinkedHashSet`**    | When you need to maintain insertion order (e.g., building a cache).   | Insertion Order    | `O(1)` (slightly slower than HashSet) | $O(1)$                           |
| **`TreeSet`**          | When you need elements sorted naturally or by a custom `Comparator`.  | Sorted (Ascending) | `O(log n)`                            | $O(\log n)$                      |

