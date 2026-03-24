---
tags:
  - "#java"
  - "#java_core"
  - collection
---
# Polymorphic_Algorithms

**Related notes:** [[Collection]]

---

In the context of the Java Collections Framework, **polymorphic algorithms** are reusable methods that can operate on different types of collections regardless of their specific underlying implementation.

The term "polymorphic" refers to the fact that the same method can take many forms — it doesn't care if you are using an `ArrayList`, a `LinkedList`, or a `Vector`, as long as the object implements the required interface.

---

## 1. Where do they live?

Most of these algorithms are provided as **static methods** in the `java.util.Collections` class. They are designed to take an interface (like `List` or `Collection`) as an argument, which allows them to work across the board.

## 2. Common Examples

Here are the most frequently used polymorphic algorithms:


- **Data Manipulation:**  
	
	- `sort(List<T> list)`: Sorts a list into ascending order
		
	- `shuffle(List<T> list)`: Randomly permutes the elements (great for games)
		
	- `reverse(List<T> list)`: Flips the order
	    
    - `fill(List<T> list, T obj)`: Replaces every element with a specific object
        
    - `copy(List<T> dest, List<T> src)`: Copies elements from one list to another. Number of elements in destination list must be greater than number of elements in source list
	    
    - `Ncopy(int n, T object)`: Creates an immutable list which contains multiple copies of the same object
		
	- **`addAll(Collection coll, T... elements)`**: Adds all specified elements to a collection
		
	- `rotate(List<?> list, int distance)`: Used for rotating elements in a List
		
	- `replaceAll(List<T> list, T oldVal, T newVal)`: Replaces all occurrences of a specific old value with a new value within a given List
		
	- `swap(List<?> list, int i, int j)`: Swaps elements within a List

- **Data inspection:**
	
	- `binarySearch(List<T> list, T key)`: Finds the index of an element in a sorted list
		
	- `min(Collection<T> coll)` and `Collections.max(Collection<T> coll)`: Find the smallest or largest element based on natural ordering
		
	- `indexOfSubList(List<?> source, List<?> target)`: Finds the starting index of a sub- list within a larger list
		
	- `disjoint()`: Used to determine if two collections have no elements in common. It returns true if they are mutually exclusive, and false otherwise
		
	- `frequency(Collection<?> c, Object o)`: Used to count the number of occurrences of a specific element within a given Collection


