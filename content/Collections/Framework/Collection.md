---
tags:
  - "#java"
  - "#java_core"
  - collection
---
# Collection

**Related notes:** [[List]] 

---

In Java, a **Collection** is essentially a specialized container that groups multiple elements into a single unit. Think of it like a digital multi-tool: instead of managing individual variables, you use a collection to store, retrieve, and manipulate data sets efficiently.

The **Java Collections Framework (JCF)** provides a unified architecture for representing and manipulating collections, reducing programming effort and increasing performance.

---

## 1. The Core Hierarchy

Most collection classes descend from the `java.util.Collection` interface. Here are the four primary "flavors" you’ll encounter:

| **Interface** | **Description**                                    | **Key Characteristic**                        |
| ------------- | -------------------------------------------------- | --------------------------------------------- |
| **List**      | An ordered sequence of elements.                   | Allows duplicates; positional access.         |
| **Set**       | A collection that cannot contain duplicates.       | High-speed uniqueness checks.                 |
| **Queue**     | Designed for holding elements prior to processing. | Typically FIFO (First-In, First-Out).         |
| **Map***      | A collection of key-value pairs.                   | Not a true `Collection`, but part of the JCF. |

![[Pasted image 20260208030750.png]]

---

## 2. Key Concepts to Remember

- **Generics:** Always use angle brackets to specify the type, e.g., `List<String> names = new ArrayList<>();`. This prevents you from accidentally putting a `Dog` object into a list of `Strings`.
    
- **Iteration:** You can easily loop through any collection using the "enhanced for-loop":

  ```
    for (String name : names) {
        System.out.println(name);
    }
  ```
  
- **The Collections Utility Class:** Don't reinvent the wheel. The `java.util.Collections` (plural) class has static methods for `sort()`, `reverse()`, and `shuffle()`.

---

## 3. Basic Methods

- **Basic & Bulk Operations:**
	
	- **`int size()`** – Returns the number of elements.
	    
	- **`boolean isEmpty()`** – Returns `true` if the collection is empty.
	    
	- **`void clear()`** – Removes all elements.
	    
	- **`boolean contains(Object o)`** – Checks if the element exists in the collection.
	    
	- **`boolean add(E e)`** – Adds an element; returns `true` if the collection changed.
	    
	- **`boolean remove(Object o)`** – Removes a single instance of the element.
	    
	- **`boolean containsAll(Collection<?> c)`** – Checks if all elements in `c` are present.
	    
	- **`boolean addAll(Collection<? extends E> c)`** – Adds all elements from `c`.
	    
	- **`boolean removeAll(Collection<?> c)`** – Removes all elements present in `c`.
	    
	- **`boolean retainAll(Collection<?> c)`** – Keeps only elements present in `c` (removes others).

**Iteration & Arrays:**
	
- **`Iterator<E> iterator()`** – Returns an iterator to traverse elements.
    
- **`Object[] toArray()`** – Returns elements as a generic object array.
    
- **`<T> T[] toArray(T[] a)`** – Returns elements as an array of type `T`.
    
- **`<T> T[] toArray(IntFunction<T[]> generator)`** – Returns elements as an array using a generator function.