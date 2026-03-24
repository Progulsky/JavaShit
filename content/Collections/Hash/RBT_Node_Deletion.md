---
tags:
  - "#java"
  - "#java_core"
---
# RBT_Node_Deletion

**Related notes:** 

---

Its a step-by-step algorithm to delete any node in Red-Black Tree. It's most complex basic operation in RBT and it can takes a lot of time and space resources cause tree starts reorganize itself

---
### Detailed Deletion Algorithm

Deleting a node from a Red-Black Tree is the most complex operation because removing a BLACK node breaks the Black Height property (Rule 5).

**Step 1: Standard BST Deletion**

- **0 Children (Leaf):** Just remove the node.
    
- **1 Child:** Remove the node and link its parent directly to its child.
    
- **2 Children:** Find the **In-Order Successor** (smallest node in the right subtree) or **In-Order Predecessor** (largest in the left subtree). Replace the target node's value with the successor's value, and then delete the original successor node.


**Step 2: Check the Color of the Removed/Moved Node**

- **If the deleted or moved node was RED:** No rules are broken. The Black Height remains exactly the same. You are done.
    
- **If the deleted or moved node was BLACK:** Removing it breaks the Black Height property (one path now has fewer black nodes). This creates a "Double Black" problem on the node that took its place (even if that node is `NULL`).


**Step 3: Fix the Double Black Violation**

To fix the missing black height, the tree looks at the **Sibling** of the "Double Black" node, as well as the sibling's children (the nephews).

_(Terminology: The **outer nephew** is the sibling's child located on the same side as the sibling itself, whereas the **inner nephew** is the sibling's child located on the opposite side)._

- **Base Case (Double Black at Root):** 
	
	- If the Double Black status bubbles all the way up to the root, simply drop the extra blackness. The root remains BLACK, the black height of the entire tree decreases by 1, and the algorithm terminates.
    
- **Case 1: Sibling is RED**
    
    - _Action:_ Recolor the Sibling to BLACK and the Parent to RED. Perform a rotation around the Parent in the direction of the Double Black node.
        
    - _Result:_ The Double Black node now has a new BLACK Sibling. The violation isn't fixed yet, but it has been successfully transformed into Case 2, 3, or 4.
    
- **Case 2: Sibling is BLACK, and both Nephews are BLACK (or NULL)**
    
    - _Action:_ Recolor the Sibling to RED.
        
    - _Result:_ The Double Black status is pushed up to the Parent. If the Parent was RED, it simply becomes BLACK and the algorithm terminates. If the Parent was already BLACK, it becomes Double Black, and you must repeat Step 3 for the new Double Black Parent.
    
- **Case 3: Sibling is BLACK, Inner Nephew is RED, Outer Nephew is BLACK**
    
    - _Action:_ Recolor the Sibling to RED and the Inner Nephew to BLACK. Perform a rotation around the Sibling in the opposite direction of the Double Black node.
        
    - _Result:_ The Inner Nephew takes the Sibling's place. This guarantees the new Sibling has a RED Outer Nephew, perfectly transforming the situation into **Case 4**. Proceed immediately to Case 4.
    
- **Case 4: Sibling is BLACK, Outer Nephew is RED**
    
    - _Action:_ Change the Sibling's color to be the exact same color as the Parent. Change the Parent's color to BLACK. Change the Outer Nephew's color to BLACK. Perform a rotation around the Parent in the direction of the Double Black node.
        
    - _Result:_ The extra black weight is successfully absorbed. The tree is perfectly balanced, and the algorithm terminates immediately.
