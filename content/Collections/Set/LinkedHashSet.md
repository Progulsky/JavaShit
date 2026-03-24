---
tags:
  - "#java"
  - "#java_core"
---
# LinkedHashSet

**Related notes:** 

---

If you liked `HashSet` for its speed but felt frustrated by its unpredictable ordering, `LinkedHashSet` is the perfect solution. It extends `HashSet` and implements the `Set` interface, offering the same fast performance while solving the ordering problem.

---

### Key Characteristics

- **Insertion Order:** Unlike a regular `HashSet`, a `LinkedHashSet` remembers the exact order in which you added elements. When you iterate through it, the elements will always come back in that same order.
    
- **No Duplicates:** Just like all `Set` implementations, it guarantees uniqueness. Re-inserting an element that is already in the set will not change its position in the insertion order.
    
- **Allows Null:** It permits exactly one `null` element.
    
- **Non-Synchronized:** Like `HashSet`, it is not thread-safe. If multiple threads access it concurrently, you must synchronize it externally (e.g., using `Collections.synchronizedSet(new LinkedHashSet<>())`).

---

### How It Works Internally

Under the hood, a `LinkedHashSet` is backed by a `LinkedHashMap`.

It uses the same hash table structure as a `HashSet` to guarantee quick lookups, but it adds a **doubly-linked list** that runs through all of its entries. Every time you add a new element, it is placed into the hash bucket (for quick searching), but it is also attached to the tail of this linked list. This linked list is what preserves the insertion order.

---

### Performance and Time Complexity

Because it relies on hashing, `LinkedHashSet` provides excellent, predictable performance:

- **Add (`add`):** `O(1)` constant time.
    
- **Remove (`remove`):** `O(1)` constant time.
    
- **Search (`contains`):** `O(1)` constant time.

**The Iteration Advantage:** While basic operations (add, remove, contains) are _slightly_ slower than a regular `HashSet` due to the overhead of maintaining the linked list pointers, **iteration is often faster**.

Iterating over a `LinkedHashSet` takes time proportional to the _size_ of the set (the actual number of elements). Iterating over a regular `HashSet` takes time proportional to its _capacity_ (the total number of buckets, including empty ones).

---

### When to Choose LinkedHashSet

You should reach for a `LinkedHashSet` when:

1. **You need uniqueness but cannot sacrifice order.** (e.g., You want to keep a history of the last 10 unique web pages a user visited).
    
2. **You are copying a collection.** It is a best practice to use a `LinkedHashSet` when copying elements from an existing `Set` to ensure the original iteration order is preserved in the copy.

> **Note:** If you need the elements to be sorted logically (like alphabetical order for Strings, or numerical order for Integers) rather than by when they were added, you would use a `TreeSet` instead.