---
tags:
  - "#java"
  - "#java_core"
  - collection
  - interface
  - list
---
# List

**Related notes:** [[Interface]], [[ArrayList]], [[LinkedList]], [[Collection]]

---

The **List** interface is a foundational component of the Java Collections Framework. It represents an **ordered sequence** of elements where the developer has precise control over where each element is inserted.

---
### Key Characteristics

- **Ordered:** Elements are stored in the exact order they are added (insertion order).
    
- **Duplicates Allowed:** You can store the same value multiple times within a single list.
    
- **Index-Based Access:** Much like an array, you can retrieve, update, or delete elements using their numerical position (starting at 0).

---
### Common Implementations

|**Implementation**|**Best For...**|**Performance Characteristics**|
|---|---|---|
|**ArrayList**|Random access & iterating|Fast retrieval by index; slower when adding/removing from the middle.|
|**LinkedList**|Frequent modifications|Fast insertions and deletions; slower retrieval by index (must traverse).|
|**Vector**|Legacy thread-safety|Synchronized (thread-safe) but generally slower; rarely used in modern non-legacy code.|

---

### Essential Methods

Since `List` provides index-based operations, it includes several methods not found in the base `Collection` interface:

- **`get(int index)`**: Retrieves the element at the specified position.
    
- **`set(int index, E element)`**: Replaces the element at the specified position.
    
- **`add(int index, E element)`**: Inserts an element at a specific spot, shifting subsequent elements to the right.
    
- **`indexOf(Object o)`**: Returns the first occurrence of the specified element.
	
- `subList(int fromIndex, int toIndex)` : Returns sub-list based on first and last index specified