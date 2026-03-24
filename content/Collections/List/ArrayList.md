---
tags:
  - "#java"
  - "#java_core"
  - collection
  - list
  - class
---
# ArrayList

**Related notes:** [[Class]], [[List]]

---

An **ArrayList** is a resizable array implementation of the `List` interface. Unlike standard arrays, which have a fixed length, an `ArrayList` dynamically grows and shrinks as you add or remove elements, making it one of the most commonly used data structures in Java.

---

### Implementation & Usage

An `ArrayList` stores objects and maintains their insertion order. You can easily create a mutable `ArrayList` from an existing collection or an immutable list.

```
import java.util.ArrayList;
import java.util.List;

// Creating a mutable copy of an immutable list
List<String> immutable = List.of("Alice", "Bob");
ArrayList<String> mutableList = new ArrayList<>(immutable);

mutableList.add("Charlie"); // Allowed
mutableList.set(1, "Robert"); // Updates "Bob" to "Robert"
mutableList.remove(0); // Removes "Alice"
```

---

### Key Features

- **Dynamic Sizing:** Automatically manages memory as elements are added.
    
- **Ordered:** Guarantees that elements stay in the order they were inserted.
    
- **Duplicates:** Allows multiple identical elements, including `null`.
    
- **Object-Only:** Only stores objects. Primitives are automatically converted via **autoboxing** (e.g., `int` becomes `Integer`).

---

### Performance: When to use ArrayList

|**Operation**|**Complexity**|**Efficiency**|
|---|---|---|
|**Random Access** (`get`/`set`)|**O(1)**|**Excellent** – Direct index access is instant.|
|**Add to End**|**O(1)**|**Very Good** – Amortized constant time.|
|**Insert/Delete (Middle)**|**O(n)**|**Poor** – Requires shifting all subsequent elements.|
|**Search** (`contains`)|**O(n)**|**Average** – Must check elements one by one.|

---

### Internal Memory Mechanics

#### 1. Lazy Allocation

When you initialize an `ArrayList` without parameters, Java doesn't allocate memory immediately. It waits for the **first** element to be added, then creates an internal array with a default capacity of **10**.

#### 2. The Growth Rule

When the internal array is full, the `ArrayList` creates a new, larger array and copies the old elements over. The growth formula is approximately **1.5x** the current size:

$$NewCapacity = OldCapacity + (OldCapacity \gg 1)$$

#### 3. Shifting

Because `ArrayList` uses a contiguous block of memory, adding or removing an element in the middle forces Java to shift every following element. This "shuffling" is why modifications in the middle of a large `ArrayList` are computationally expensive.

---

### Pro Tips for Efficiency

- **`ensureCapacity(int min)`:** If you know you'll store 10,000 items, call this first to prevent multiple expensive "resize-and-copy" cycles.
    
- **`trimToSize()`:** If you've finished a list and want to save memory, use this to shrink the internal array to exactly match the current number of elements.
    
- **Cache Locality:** Because data is stored contiguously, `ArrayList` is significantly faster than `LinkedList` for iteration, as it plays nicely with the CPU's cache.