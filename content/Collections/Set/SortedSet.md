---
tags:
  - "#java"
  - "#java_core"
---
# SortedSet

**Related notes:** 

---

`SortedSet` interface introduces a strict set of rules for **ordering**. It extends the standard `Set` interface and guarantees that all elements within it are constantly kept in a sorted sequence.

---

### Key Characteristics

- **Automatic Sorting:** The moment you add an element to a `SortedSet`, it is automatically placed in its correct sorted position.
    
- **Two Sorting Methods:** It sorts elements either by their _natural ordering_ (e.g., A-Z for Strings, 1-10 for numbers) or by a custom `Comparator` that you provide when creating the implementing collection.
    
- **No Duplicates:** It strictly adheres to the `Set` contract; duplicate elements are ignored.
    
- **Type Restrictions:** All elements inserted into a `SortedSet` must be mutually comparable. For example, you cannot mix `String` and `Integer` objects, or it will throw a `ClassCastException`

---

### The Power of Range Views

The real magic of the `SortedSet` interface lies in its unique methods that allow you to carve out specific "views" or chunks of your data. These are incredibly powerful for range queries.

|**Method**|**What it does**|
|---|---|
|**`first()`**|Returns the absolute lowest (first) element currently in the set.|
|**`last()`**|Returns the absolute highest (last) element currently in the set.|
|**`headSet(toElement)`**|Returns a view of the set containing everything strictly _less than_ the `toElement`.|
|**`tailSet(fromElement)`**|Returns a view of the set containing everything _greater than or equal to_ the `fromElement`.|
|**`subSet(from, to)`**|Returns a view of the set from `from` (inclusive) up to `to` (exclusive).|
|**`comparator()`**|Returns the `Comparator` being used to sort the set, or `null` if it is using natural ordering.|

> **Crucial Detail:** The collections returned by `headSet`, `tailSet`, and `subSet` are **views** of the original set, not copies. If you make a change to the `subSet`, that change is immediately reflected in the original `SortedSet`, and vice versa!

---

### Common Implementations

Since `SortedSet` is an interface, you will typically use one of these two classes to actually create the object:

1. **`TreeSet`:** The standard, go-to implementation for general-purpose sorted sets (not thread-safe).
    
2. **`ConcurrentSkipListSet`:** A thread-safe implementation used in highly concurrent, multi-threaded applications.