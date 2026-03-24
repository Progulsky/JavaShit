---
tags:
  - "#java"
  - "#java_core"
  - fundamentals
  - control_flow
  - loops
  - collection
---
# For-Each_Statement

**Related notes:** [[For_Statement]], [[Code_Block]], [[Scope]], [[Array]], [[Collection]]

---

This is a simplified way to iterate through elements in **arrays** and **collections**.

---
### **Key Rules:**

- **Temporary Element:** The `element` is a temporary variable that takes the value of each item (must match the array's data type).
    
- **Automatic:** The loop runs automatically from the first to the last element.
    
- **No Modification:** You **cannot modify** the Array or list elements directly (e.g., `element = value;` does not change the original array).
    
- **No Index:** You **cannot access the index** of the current element.


```
for (type element : arrayOrCollection) {
    // Use element
}

// EXAMPLE
int[] numbers = {10, 20, 30, 40};
for (int num : numbers) {
    System.out.println(num);
}
```