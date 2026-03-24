---
tags:
  - "#java"
  - "#java_core"
---
# RBT_Node_Insertion

**Related notes:** 

---

Detailed guide how to insert any node in any position in Red-Black Tree. This operation can be either very fast and easy or truly complex (like deletion).

---
### Detailed Insertion Algorithm (Building the Tree)

When inserting a new element, the tree follows a strict step-by-step algorithm to decide whether to recolor or rotate.

**Step 1: Standard BST Insertion**

Find the correct spot for the new node following standard Binary Search Tree rules (smaller values to the left, larger to the right).


**Step 2: Color the New Node**

Always color the newly inserted node **RED**. (This preserves the Black Height property). If the new node is the Root, simply color it BLACK and you are done.


**Step 3: Check for Violations**

If the new node's **Parent is BLACK**, no rules are broken. You are done. If the new node's **Parent is RED**, you have a "Double Red" violation (Rule 4). To fix it, you must look at the color of the new node's **Uncle** (the sibling of its Parent).

- **Case 1: The Uncle is RED (Recoloring)**
    
    1. Change the color of the **Parent** and **Uncle** to **BLACK**.
        
    2. Change the color of the **Grandparent** to **RED**.
        
    3. _Action:_ The current violation is fixed, but making the Grandparent RED might cause a new Double Red violation higher up. Move your focus to the Grandparent and repeat Step 3 until the root is reached (ensuring the root remains BLACK).
    
- **Case 2: The Uncle is BLACK (or NULL) & forms a "Straight Line" (Rotation)**
    
    _Condition:_ The Grandparent, Parent, and New Node form a straight line (e.g., Left-Left or Right-Right).
    
    1. Perform a single **Rotation** around the **Grandparent** (pushing the Grandparent down and bringing the Parent up).
        
    2. Swap the colors of the **Parent** (now on top) and the **Grandparent** (now pulled down).
        
    3. _Action:_ The Parent becomes BLACK, the Grandparent becomes RED. The tree is now balanced, and the algorithm is finished.
    
- **Case 3: The Uncle is BLACK (or NULL) & forms a "Zig-Zag" (Double Rotation)**
    
    _Condition:_ The Grandparent, Parent, and New Node form an angle (e.g., Left-Right or Right-Left).
    
    1. Perform a single **Rotation** around the **Parent** to convert the Zig-Zag shape into a Straight Line. To balance the tree, you pull the Parent down and elevate its child. In a **Right Rotation**, the Parent is pulled down to the right, and the Left Child moves up. If the elevated child already had an "inner" right child (an orphan), that orphan disconnects and reattaches as the inner child of the pulled-down Parent. A **Left Rotation** is the exact mirror image.
        
    2. The New Node and the Parent swap positions.
        
    3. _Action:_ You are now exactly in **Case 2**. Proceed immediately to Case 2 to finish the repair.
