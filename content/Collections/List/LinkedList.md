---
tags:
  - "#java"
  - "#java_core"
  - collection
  - list
  - class
---
# LinkedList

**Related notes:** [[Class]], [[List]]

---

A **LinkedList** is a linear data structure provided by the Java Collections Framework (JCF). Unlike an `ArrayList`, which uses a contiguous array, a `LinkedList` stores elements in non-contiguous memory locations. It belongs to the `java.util` package and uniquely implements both the **List** and **Deque** interfaces, allowing it to function as a list, a stack, or a queue.

---

### Implementation & Usage

A `LinkedList` is composed of "nodes" that point to one another. Because it implements `Deque`, it provides specific methods for interacting with the head and tail of the list.

```
import java.util.LinkedList;

LinkedList<String> list = new LinkedList<>();

// Adding elements with specialized Deque methods
list.add("Apple");
list.addFirst("Mango");  // Adds to the very front
list.addLast("Orange");   // Adds to the very end

System.out.println(list); // [Mango, Apple, Orange]

// Efficient removal from the head
list.removeFirst(); 
```

---

### Key Features

- **Doubly Linked:** Each node contains a reference to both the **previous** and the **next** node, allowing for bidirectional traversal.
    
- **Dynamic Size:** It grows and shrinks seamlessly without the need for expensive array reallocations or "growth formulas."
    
- **Efficient Modifications:** Inserting or deleting elements—especially at the ends—is extremely fast (O(1)).
    
- **Sequential Access:** To find an element, Java must start at the beginning (or end) and follow the pointers, making random access (O(n)) much slower than an array-based structure.

---

### Performance: When to Use LinkedList

|**Operation**|**Complexity**|**Efficiency**|
|---|---|---|
|**Random Access** (`get`/`set`)|**O(n)**|**Poor** – Must traverse node by node.|
|**Add/Remove at Ends**|**O(1)**|**Excellent** – Only involves updating pointers.|
|**Insert/Delete (Middle)**|**O(n)**|**Average** – Fast once the position is found, but finding it takes time.|
|**Memory Overhead**|**High**|**Poor** – Requires extra memory for two pointers per element.|

---

### Internal Memory & Node Structure

Each element in a `LinkedList` is wrapped in a private static **Node** object on the heap. This structure is what allows the list to be non-contiguous.

```
private static class Node<E> {
    E item;       // The actual data
    Node<E> next; // Reference to the next node
    Node<E> prev; // Reference to the previous node
}
```

#### How it works:

1. **Traversal:** To reach the 5th element, the JVM starts at the `first` pointer and follows `.next` five times. It cannot "jump" to an index.
    
2. **Insertion:** To insert a node, Java simply breaks the existing links between two nodes and re-routes them through the `NewNode`. No other elements are shifted or copied.

---

### Why Choose LinkedList?

- **Queue/Deque Implementation:** Ideal for FIFO (First-In-First-Out) or LIFO (Last-In-First-Out) operations using `offer()`, `poll()`, `push()`, and `pop()`.
    
- **Predictable Growth:** Since there is no internal array to resize, you never encounter the occasional "lag" caused by `ArrayList` copying its contents to a larger array.
    
- **Iterator Efficiency:** When using a `ListIterator`, you can add or remove elements while traversing the list in O(1) time.