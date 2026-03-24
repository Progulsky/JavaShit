---
tags:
  - "#java"
  - "#java_core"
  - class
  - class_subtype
  - data_carrier
  - immutability
---
# Record

**Related notes:** [[Class]], [[POJO]], [[Encapsulation]]

---

A **Record** is a specialized Java class type designed to be a compact, immutable data carrier. It functions similarly to a POJO but significantly reduces boilerplate code by using the `record` keyword.

---

### When to Use a Record

- **Immutability:** For data that should not change once it is created.
    
- **Boilerplate Reduction:** To eliminate the repetitive code required in standard POJOs.
    
- **Value Objects:** Ideal for configurations, API responses, Data Transfer Objects (DTOs), and domain models.

---

### Key Functionality

- **Automatic Generation:** Java automatically generates the constructor, getters, `equals()`, `hashCode()`, and `toString()`.
    
- **Strict Immutability:** All fields are implicitly `final`; they cannot be modified after object creation.
    
- **Flexibility:** While automated, records still allow for custom methods and logic.
    
- **Constraints:** Records **cannot extend** other classes and **do not allow setters**.

---

### Anatomy of a Record

A record consists of:

1. An **access modifier** (e.g., `public`).
    
2. The `record` **keyword**.
    
3. A **header** containing comma-delimited components. These components define the state and tell the compiler how to generate the class members.

---
### Implementation Comparison

A single line of record code is functionally equivalent to a verbose final class

```
// Compact Record Definition
public record Person(String name, int age) {}

// Equivalent Standard Class
public final class Person {
    private final String name;
    private final int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String name() { return name; }
    public int age() { return age; }

    @Override
    public String toString() {
        return "Person[name=" + name + ", age=" + age + "]";
    }

    @Override
    public boolean equals(Object o) { /* ... */ }

    @Override
    public int hashCode() { /* ... */ }
}
```

---

### Accessing Data

In a record, getters are not prefixed with "get" (e.g., `getName()`). Instead, the method names match the field names exactly.

```
public record Person(String name, int age) {}

public class Main {
    public static void main(String[] args) {
        Person p = new Person("Alice", 30);

        // Accessing values using component-named methods
        System.out.println(p.name()); // Output: Alice
        System.out.println(p.age());  // Output: 30
    }
}
```