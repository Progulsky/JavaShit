---
tags:
  - "#java"
  - "#java_core"
---
# Bucket_System

**Related notes:** 

---

The "bucket system" is the internal architecture Java uses to implement `HashMap` and `HashSet`. It is essentially a clever way to map a potentially infinite universe of objects to a finite array of slots (buckets) to achieve lightning-fast retrieval speeds.

---

### 1. The Core Structure: An Array of Nodes

At the lowest level, a `HashMap` is simply an array (often called the **table**).

```
transient Node<K,V>[] table;
```

- **The Bucket:** Each index in this array is a "bucket."
    
- **The Content:** Each bucket doesn't store just one Key-Value pair; it stores the **head of a data structure** (initially a Linked List).
    
- **The Node:** The objects stored in the bucket are of type `Node<K,V>`. A Node contains four things:
    
    1. The **Hash** (cached for performance).
        
    2. The **Key**.
        
    3. The **Value**.
        
    4. A **Next** pointer (reference to the next node in the bucket).

---

### 2. How an Object Finds its Bucket (The Indexing)

When you call `map.put(key, value)`, Java needs to decide which array index (bucket) to drop this node into.

1. **Hashing:** Java calculates the `key.hashCode()`.
    
2. **Perturbation (The "Hash Spread"):** To prevent poor hash codes from clumping together, Java XORs the hash with its upper bits: `(h = key.hashCode()) ^ (h >>> 16)`.
    
3. **Index Calculation:** Java uses a bitwise operation to find the index:
    $$Index = (n - 1) \& hash$$
    _(Where $n$ is the current size of the array)._

> **Note:** The array size ($n$) is always a power of 2 (16, 32, 64...). This allows Java to use the bitwise `&` operator instead of the slower modulo `%` operator to wrap the hash code into the array bounds.

---

### 3. Inside the Bucket: Collision Handling

What happens if two different keys calculate to the same bucket index? This is a **collision**. Java handles this in two phases depending on how crowded the bucket is.

#### Phase 1: The Linked List (Standard)

Initially, a bucket is just a Singly Linked List.

- If Bucket 4 is empty, the new Node becomes the head.
    
- If Bucket 4 already has a Node (collision), Java traverses the list. If the key exists, it updates the value. If not, it appends the new Node to the end.
    
- **Performance:** $O(n)$ relative to the number of items _in that specific bucket_.

#### Phase 2: Treeification (Java 8+ Optimization)

If a single bucket gets too heavy, traversing a long Linked List becomes slow ($O(n)$). To fix this, Java 8 introduced **Treeification**.

- **The Threshold:** If a bucket reaches **8 nodes** (the `TREEIFY_THRESHOLD`) and the total array capacity is at least 64, the Linked List transforms into a **Red-Black Tree**.
    
- **The Benefit:** A Red-Black Tree allows for $O(\log n)$ retrieval speed instead of $O(n)$. This prevents performance degradation even if massive collisions occur (e.g., a "Hash DoS" attack).
    
- **Untreeification:** If you remove elements and the bucket size drops to **6**, the Tree converts back to a Linked List to save memory.

---

### 4. Retrieving an Object from a "Collision Bucket"

When you call `map.get(key)`, Java calculates the index and jumps to the specific bucket. If that bucket contains multiple nodes (a **collision**), Java must identify exactly which node belongs to you.

It iterates through the **Linked List** (or **Red-Black Tree**) and performs a strict **3-step check** for every single node:

#### Step 1: The Hash Check (Fast Filter)

First, Java compares the **hash code** of your search key with the hash code stored in the node.

- **Why?** Comparing integers is extremely fast.
    
- **Logic:** `if (node.hash != key.hashCode())` $\rightarrow$ **Skip this node immediately.** It cannot be the right object.

#### Step 2: The Reference Check (Optimization)

If the hashes match, Java checks if the keys are the **same object in memory** using the `==` operator.

- **Why?** If the memory addresses are the same, it is definitely the same key. We don't need to waste time running the potentially heavy `equals()` method.
    
- **Logic:** `if (node.key == key)` $\rightarrow$ **Found it! Return the Value.**

#### Step 3: The Equality Check (The Final Verdict)

If the addresses are different (which is common for Strings or custom objects created at different times), Java calls the **`equals()`** method.

- **Why?** This checks the **logical content** of the key (e.g., is the user ID the same?).
    
- **Logic:** `if (key.equals(node.key))` $\rightarrow$ **Found it! Return the Value.**

|**Hash Codes**|**Addresses (==)**|**equals()**|**HashMap Action**|**Interpretation**|
|---|---|---|---|---|
|**Different**|_(Ignored)_|_(Ignored)_|**Different Buckets**|Definitely different objects. No conflict.|
|**Same**|**True**|_(Not called)_|**Overwrite Value**|Physically the **same object instance** in memory.|
|**Same**|**False**|**True**|**Overwrite Value**|**Logical Duplicates.** Different objects in memory, but they mean the same thing (e.g., two Strings "Java").|
|**Same**|**False**|**False**|**Append to Chain**|**TRUE COLLISION.** Different objects that just happened to have the same hash. Stored together in a Linked List/Tree.|

---

### 5. The `resize()` Operation

The bucket array has a fixed size. As you add more elements, the buckets fill up, and collisions increase. To maintain speed, the map must resize.

- **Load Factor:** The default load factor is **0.75**. This means if the map is 75% full (e.g., 12 entries in a size-16 map), it triggers a resize.
    
- **Doubling:** The array size doubles (e.g., 16 $\rightarrow$ 32).
    
- **Rehashing:** This is the expensive part. Since the array size ($n$) has changed, the index formula `(n - 1) & hash` yields different results. Every single node in the map must be recalculated and moved to its new bucket.

---

### Summary Visualization

Imagine a HashMap with an array size of 4.

|**Index**|**Bucket Contents (Simplified)**|
|---|---|
|**0**|`[Key: "Apple"]` $\rightarrow$ `null`|
|**1**|`null` (Empty)|
|**2**|`[Key: "Banana"]` $\rightarrow$ `[Key: "Grapes"]` $\rightarrow$ `[Key: "Mango"]`|
|**3**|`[Key: "Orange"]` $\rightarrow$ `null`|

- **Bucket 0:** Has 1 item.
    
- **Bucket 1:** Is empty.
    
- **Bucket 2:** Has a collision. Three items are chained in a Linked List.
    
- **Bucket 3:** Has 1 item.

If we added 6 more items to **Bucket 2**, it would convert into a Red-Black Tree structure internally.

---

### Why This Matters for You

1. **Time Complexity:**
    
    - **Best Case:** $O(1)$ (No collisions).
        
    - **Worst Case (Java 7):** $O(n)$ (All keys hit the same bucket).
        
    - **Worst Case (Java 8+):** $O(\log n)$ (Red-Black Tree protection).
        
2. **Immutability:** If you use a mutable object as a key and change it, its Hash Code changes. Java will look for it in the _new_ calculated bucket, but the object is still sitting in the _old_ bucket. **The map effectively "loses" the data.**