---
tags:
  - "#java"
  - "#java_core"
  - class
---
# Array

**Related notes:** [[Class]], [[ArrayList]]

---

An **array** is a fixed-size container object that holds a specific number of elements of a **single data type**. Arrays are stored in **contiguous memory locations**, which makes them incredibly efficient for accessing data via an index.

---

### Declaration and Initialization

In Java, arrays are treated as objects. You can initialize them by specifying a size or by using an initializer list.

- **Fixed Size:** Once an array is instantiated, its length **cannot be changed**. If you need more space, you must create a new, larger array and copy the elements over.
    
- **Anonymous Array Initializers:** The shorthand `{val1, val2}` can only be used during the initial declaration.

```
// Preferred declaration style
int[] numbers = new int[5]; // Initialized with default values (0 for int)

// Anonymous initializer (declaration and assignment in one step)
int[] primes = {2, 3, 5, 7, 11}; 
```

### Accessing and Iterating

Array indices are **zero-based**, meaning the first element is at `[0]` and the last is at `[length - 1]`.

- **`.length` Property:** Use this to get the capacity of the array. Note that it is a **final variable**, not a method, so there are no parentheses.
    
- **Enhanced For-Loop:** Also known as the "for-each" loop, this is the cleanest way to read elements when you don't need the index value.

---

### The `java.util.Arrays` Utility Class

Because raw arrays have limited built-in functionality, Java provides a utility class full of **static methods** to handle common tasks.

|**Method**|**Description**|
|---|---|
|**`toString(arr)`**|Converts the array into a human-readable String like `[1, 2, 3]`.|
|**`sort(arr)`**|Sorts the array in ascending order (Dual-Pivot Quicksort).|
|**`copyOf(arr, newLen)`**|Creates a new array, copies original data, and pads/truncates to `newLen`.|
|**`equals(arr1, arr2)`**|Checks if two arrays have the same length and identical elements in the same order.|
|**`binarySearch(arr, val)`**|Rapidly finds the index of a value. **Requires the array to be sorted first.**|

---

### Object and Multidimensional Arrays

#### Object Arrays (`Object[]`)

Since all classes inherit from `Object`, an `Object[]` can store a mix of different types (Strings, Integers, etc.).

- **Autoboxing:** Primitives (like `int`) are automatically converted to their wrapper classes (`Integer`) when stored in an Object array.
    
- **Risk:** You lose **Type Safety**. Accessing specific methods requires manual **downcasting**, which can lead to `ClassCastException`.

#### Multidimensional Arrays

A multidimensional array is simply an **array of arrays**. A 2D array is often visualized as a grid of rows and columns.

```
int[][] matrix = {
    {1, 2, 3}, // Row 0
    {4, 5, 6}, // Row 1
    {7, 8, 9}  // Row 2
};

// Accessing: matrix[row][column]
System.out.println(matrix[1][2]); // Prints 6
```

> **Pro-Tip:** In Java, 2D arrays can be "jagged"—meaning each row can have a different number of columns.