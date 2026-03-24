---
tags:
  - "#java"
  - "#java_core"
  - interface
  - collection
---
# Comparator

**Related notes:** [[Interface]], [[Collection]]

---

A **Comparator** is a functional interface in the `java.util` package that allows you to define **custom sorting logic** for your objects. While `Comparable` is used to define a class's "natural" (default) order from _within_ the class, `Comparator` allows you to define as many different sorting strategies as you want _outside_ of the class.

---

### How `compare()` Works

The core of a Comparator is the `int compare(T o1, T o2)` method. It evaluates two objects to determine their relative order:

|**Result**|**Logic**|**Sort Placement**|
|---|---|---|
|**$0$**|`o1` is equal to `o2`|No change in relative order.|
|**Negative ($< 0$)**|`o1` is "smaller" than `o2`|`o1` is placed **before** `o2`.|
|**Positive ($> 0$)**|`o1` is "larger" than `o2`|`o1` is placed **after** `o2`.|

---

### Implementation Strategies

Because `Comparator` is a functional interface, you have several ways to implement it, ranging from traditional classes to modern, concise lambdas.

#### 1. Traditional Class Implementation

Useful if the sorting logic is complex and needs to be reused in multiple places.

```
class AgeComparator implements Comparator<Person> {
    @Override
    public int compare(Person p1, Person p2) {
        return Integer.compare(p1.age, p2.age);
    }
}
```

#### 2. Lambda Expressions (Modern)

Since Java 8, this is the most common way to write a Comparator on the fly.

```
// Sort by name using a lambda
people.sort((p1, p2) -> p1.name.compareTo(p2.name));
```

#### 3. Method References & Factory Methods

Java provides static methods in the `Comparator` interface to make code even more readable.

```
// Very clean: Using Comparator.comparing
people.sort(Comparator.comparing(p -> p.name));

// Even cleaner: Using method references
people.sort(Comparator.comparing(Person::getName));
```

---

### Why Use Comparator?

- **Decoupling:** You don't need to modify the source code of the class you are sorting. This is vital when working with third-party libraries.
    
- **Multiple Sort Orders:** You can sort the same list of `Products` by `price`, then by `rating`, then by `brand` simply by passing different Comparators.
    
- **Chaining:** You can easily chain comparisons. For example, "Sort by name; if the names are the same, sort by age."

```
people.sort(Comparator.comparing(Person::getName).thenComparing(Person::getAge));
```

---

### Helper Methods in `Comparator`

The `Comparator` interface includes several **default methods** that allow you to compose, reverse, and fine-tune sorting logic without writing manual `if-else` blocks or handling `null` values manually.

#### 1. `reversed()`

Returns a comparator that imposes the reverse ordering of the current one.

```
// Sort by age in descending order
people.sort(Comparator.comparing(Person::getAge).reversed());
```

#### 2. `thenComparing()`

Used for **lexicographical sorting** (multi-level sorting). If the first comparator considers two elements equal, it moves to the next one.

```
// Sort by Last Name, then by First Name if Last Names are identical
people.sort(Comparator.comparing(Person::getLastName)
                      .thenComparing(Person::getFirstName));
```

#### 3. `nullsFirst()` and `nullsSecond()`

These static methods handle cases where the collection contains `null` elements, preventing a `NullPointerException`.

```
// Nulls go to the end of the list, valid objects are sorted by name
people.sort(Comparator.nullsLast(Comparator.comparing(Person::getName)));
```

#### 4. `thenComparingInt()`, `thenComparingDouble()`, etc.

Specialized versions of `thenComparing` to avoid **autoboxing** (conversions between primitive types and their Wrapper classes), which improves performance.

```
people.sort(Comparator.comparing(Person::getName)
                      .thenComparingInt(Person::getAge)); 
```

#### 5. `Comparator.comparing(Function)`

This is the most common way to create a comparator. It takes a function that extracts a sort key and returns a `Comparator` for that key type.

```
// Logic: Extract the name (String) and compare names
Comparator<Person> nameComparator = Comparator.comparing(Person::getName);
```