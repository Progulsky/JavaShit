---
tags:
  - "#java"
  - "#java_core"
---
# HashSet

**Related notes:** 

---

In Java, a `HashSet` is one of the most popular classes within the Java Collections Framework. It implements the `Set` interface and is used to store a collection of unique items. Under the hood, a `HashSet` is actually backed by a `HashMap`.

---

### Key Characteristics

- **No Duplicates:** It guarantees that no two identical elements exist in the set. If you try to add a duplicate element, the `add()` method simply returns `false` and the set remains unchanged.
    
- **Unordered:** It makes no guarantees about the iteration order of the elements. The order may even change over time as the collection grows and rehashes.
    
- **Allows Null:** It permits exactly one `null` element.
    
- **Non-Synchronized:** It is not thread-safe. If multiple threads access a `HashSet` concurrently and at least one modifies it, it must be synchronized externally.

> **Note:** If you need a thread-safe version, you can wrap it using `Collections.synchronizedSet(new HashSet<>())` or use `ConcurrentHashMap.newKeySet()`.

---

### How It Works Internally

When you use a `HashSet`, you are essentially using a `HashMap` where the elements you add are stored as the _keys_ in the map. A constant dummy object (usually an empty `Object` called `PRESENT`) is used as the _value_ for all keys.

If you are storing custom objects in a `HashSet`, you **must** override both `hashCode()` and `equals()` in your class for the set to function correctly.

---

### Performance and Time Complexity

Because it uses hashing, `HashSet` offers excellent performance for basic operations, assuming your hash function disperses elements properly among the buckets:

- **Add (`add`):** `O(1)` constant time.
    
- **Remove (`remove`):** `O(1)` constant time.
    
- **Search (`contains`):** `O(1)` constant time.

_Worst-case scenario:_ If all elements hash to the same bucket (terrible hash function), performance degrades to `O(n)` or `O(log n)`

---

### Tuning a HashSet

When you create a `HashSet`, you can pass two parameters that affect its performance and memory usage:

- **Initial Capacity:** The number of buckets created when the set is initialized (default is 16).
    
- **Load Factor:** A measure of how full the set is allowed to get before its capacity is automatically doubled (default is 0.75).

If you know you are going to add 1,000 elements, it is more efficient to set a higher initial capacity to avoid the overhead of constant resizing (rehashing) as the set grows.
