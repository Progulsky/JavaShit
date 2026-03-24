---
tags:
  - "#java"
  - "#java_core"
  - interface
  - collection
---
# Comparable

**Related notes:** [[Interface]], [[Collection]]

---

**Comparable** is a built-in generic interface located in the `java.lang` package. It is used to define the **natural ordering** of objects. When a class implements `Comparable`, it is essentially saying, "I know how to compare myself to other objects of my type."

---

### The `compareTo()` Method

The core of this interface is the `int compareTo(T o)` method. It compares the current object 
(`this`) with the object passed as an argument. The integer result determines the relative order:

|**Result**|**Meaning**|**Sort Order**|
|---|---|---|
|**$0$**|Both objects are equal|Stays in place|
|**Negative ($< 0$)**|`this` is **less than** the other object|`this` comes **before** the other|
|**Positive ($> 0$)**|`this` is **greater than** the other object|`this` comes **after** the other|

---

### Implementation Example

To use it, you implement the interface and provide the logic for your "natural order" (e.g., sorting students by their age).

```
class Student implements Comparable<Student> {
    private String name;
    private int age;

    public Student(String name, int age) {
        this.name = name;
        this.age = age;
    }

    // Defining natural order by age
    @Override
    public int compareTo(Student other) {
        // Option 1: Manual comparison
        // return this.age - other.age; 
        
        // Option 2: Using Integer utility (Best Practice)
        return Integer.compare(this.age, other.age);
    }

    @Override
    public String toString() {
        return name + " (" + age + ")";
    }
}
```

#### Usage with Collections

Once implemented, you can use standard sorting utilities without any extra configuration:

```
List<Student> students = new ArrayList<>(List.of(...));
Collections.sort(students); // Automatically uses Student's compareTo()
```

---

### Natural Ordering in Strings

The `String` class implements `Comparable` using **Lexicographical Order** (dictionary order based on Unicode values). It compares characters one by one from left to right.

```
"cat".compareTo("car"); 
// 'c' vs 'c' (0)
// 'a' vs 'a' (0)
// 't' (Unicode 116) vs 'r' (Unicode 114) 
// Result: 2 (Positive, so "cat" > "car")
```

---

### Key Takeaways

- **Single Order:** A class can only have **one** natural ordering (one `compareTo` implementation).
    
- **Automatic Integration:** Highly beneficial for use with sorted collections like `TreeSet` or `TreeMap`.
    
- **Consistency:** It is a best practice to ensure that `(x.compareTo(y) == 0)` is consistent with `x.equals(y)`.

> **Peer Note:** While `Comparable` is great for a default sort order, if you need to sort by different criteria (like by name _sometimes_ and by age _other times_), you should use the **Comparator** interface instead.