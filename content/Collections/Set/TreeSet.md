---
tags:
  - "#java"
  - "#java_core"
---
# TreeSet

**Related notes:** 

---

If you need a collection that guarantees uniqueness _and_ keeps everything perfectly sorted, `TreeSet` is the tool for the job. It implements the `Set` interface, but more specifically, it implements the `SortedSet` and `NavigableSet` interfaces, which give it powerful sorting and navigation capabilities.

---

### Key Characteristics

- **Sorted Order:** Elements in a `TreeSet` are always sorted. By default, they are sorted according to their _natural ordering_ (e.g., alphabetically for Strings, numerically for Integers). You can also provide a custom `Comparator` when creating the set to define your own sorting rules.
    
- **No Duplicates:** Like all `Set` implementations, it does not allow duplicate elements.
    
- **No Nulls Allowed:** Unlike `HashSet` and `LinkedHashSet`, a `TreeSet` **does not allow `null` elements**. Because it constantly compares elements to keep them sorted, inserting a `null` will instantly throw a `NullPointerException`.
    
- **Non-Synchronized:** It is not thread-safe. If multiple threads access it concurrently, it must be synchronized externally.

---

### How It Works Internally

Under the hood, a `TreeSet` is backed by a `TreeMap`, which is implemented as a **Red-Black Tree**.

Because it relies on tree nodes rather than a hash table, `TreeSet` does **not** use the `hashCode()` method at all. Instead, it relies entirely on the `compareTo()` method (from the `Comparable` interface) or a custom `Comparator` to figure out where an element belongs in the tree and to check for duplicates.

---

### Performance and Time Complexity

Because of the Red-Black tree structure, `TreeSet` is slower than `HashSet` for basic operations, but it guarantees consistent logarithmic time complexity:

- **Add (`add`):** `O(log n)` time.
    
- **Remove (`remove`):** `O(log n)` time.
    
- **Search (`contains`):** `O(log n)` time.

While `O(log n)` is slightly slower than the `O(1)` of a `HashSet`, it is still incredibly fast, even for millions of elements.

---

### When to Choose TreeSet

You should choose a `TreeSet` when:

1. **You need your data to be strictly sorted at all times.** 
	
2. **You need to perform range queries** (e.g., "give me all numbers between 50 and 100" using `subSet()`) or find closest matches (using `lower()`, `higher()`, etc.).