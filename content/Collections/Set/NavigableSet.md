---
tags:
  - "#java"
  - "#java_core"
---
# NavigableSet

**Related notes:** 

---

The `NavigableSet` interface in the Java Collections Framework extends the `SortedSet` interface. While a `SortedSet` guarantees that elements are kept in a specific order and provides basic range views, `NavigableSet` introduces advanced navigation methods. These methods allow for finding the closest matches for specific search targets, making it highly effective for queries based on proximity rather than exact matches.

---

### Core Navigation Methods

The primary advantage of a `NavigableSet` lies in four methods designed to locate elements relative to a given value, even if that value does not exist within the set itself.

|**Method**|**Description**|
|---|---|
|**`lower(E e)`**|Returns the greatest element strictly **less than** the given element `e`, or `null` if there is no such element.|
|**`floor(E e)`**|Returns the greatest element **less than or equal to** the given element `e`, or `null` if there is no such element.|
|**`ceiling(E e)`**|Returns the least element **greater than or equal to** the given element `e`, or `null` if there is no such element.|
|**`higher(E e)`**|Returns the least element strictly **greater than** the given element `e`, or `null` if there is no such element.|

---

### Extraction and Reversal Methods

In addition to searching, `NavigableSet` provides methods to safely extract elements from the ends of the collection and to view the collection in reverse order.

- **`pollFirst()`:** Retrieves and removes the first (lowest) element, or returns `null` if the set is empty.
    
- **`pollLast()`:** Retrieves and removes the last (highest) element, or returns `null` if the set is empty.
    
- **`descendingSet()`:** Returns a reverse-order view of the elements contained in the set. The returned set is backed by the original set, meaning changes to one are reflected in the other.
    
- **`descendingIterator()`:** Returns an iterator that traverses the set in descending order.