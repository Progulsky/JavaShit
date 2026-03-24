---
tags:
  - "#java"
  - "#java_core"
---
# Red-Black_Tree

**Related notes:** 

---

A **Red-Black Tree** is a type of self-balancing Binary Search Tree (BST). It is one of the most important data structures in computer science and forms the backbone of several core components in the Java Collections Framework.

Because a standard Binary Search Tree can become unbalanced (e.g., if you insert already-sorted data, it essentially becomes a slow linked list), a Red-Black tree applies specific rules to guarantee that the tree remains relatively balanced. This ensures fast, predictable performance.

---

### Where does Java use Red-Black Trees?

In Java, you generally don't interact with a Red-Black Tree directly by name. Instead, Java uses it under the hood for:

1. **`TreeMap`:** This map implementation stores key-value pairs sorted by their keys. The entire structure is a Red-Black Tree.
    
2. **`TreeSet`:** As mentioned in the previous response, this is a sorted set. Internally, a `TreeSet` is actually just a wrapper around a `TreeMap` (it stores the set elements as keys, and a dummy object as the values).
    
3. **`HashMap` (since Java 8):** To protect against poor hash functions or malicious collisions, Java 8 changed how `HashMap` handles collisions. If too many elements end up in the same "bucket" (specifically, 8 or more elements), the internal structure of that bucket changes from a simple Linked List to a Red-Black Tree.

---

### The 5 Rules of a Red-Black Tree

To maintain its balance, a Red-Black Tree assigns a "color" (red or black) to every node and strictly enforces the following five properties. If any of these rules are broken during an insertion or deletion, the tree automatically reorganizes itself.

1. **Node Color:** Every node is colored either **Red** or **Black**.
    
2. **Root Property:** The root of the tree is always **Black**.
    
3. **Leaf Property:** Every leaf (in Red-Black trees, leaves are conceptual `NULL` nodes at the very bottom) is **Black**.
    
4. **Red Property (No Double Reds):** If a node is **Red**, then both of its children must be **Black**. You cannot have two consecutive Red nodes on any path from the root to a leaf.
    
5. **Black Height Property:** Every simple path from a given node to any of its descendant leaves must contain the exact same number of **Black** nodes.

**Why do these rules matter?** Combined, Rule 4 and Rule 5 guarantee that the longest path from the root to any leaf is no more than twice as long as the shortest path. This enforces the "self-balancing" nature of the tree.

---

### Performance & Time Complexity

Because the tree guarantees a balanced depth, its time complexity is highly predictable. Where a poorly built, unbalanced standard BST can degrade to $O(n)$ time, a Red-Black tree guarantees logarithmic time complexity.

|**Operation**|**Worst-Case Time Complexity**|
|---|---|
|**Search / Contains**|$O(\log n)$|
|**Insert**|$O(\log n)$|
|**Delete**|$O(\log n)$|

---

### Red-Black Trees vs. AVL Trees

You might have heard of another self-balancing tree called an AVL Tree. While AVL trees are strictly more balanced than Red-Black trees (making their lookups marginally faster), Java chose Red-Black trees for its standard library.

**Why?** Because AVL trees are _so_ rigidly balanced that inserting and deleting elements requires too many rotations. Red-Black trees strike a perfect compromise: they are balanced enough to guarantee $O(\log n)$ lookups, but relaxed enough that inserts and deletes are much faster.