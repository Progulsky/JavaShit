---
tags:
  - "#java"
  - "#java_core"
  - class
  - class_subtype
  - data_carrier
  - immutability
---
# POJO

**Related notes:** [[Class]], [[Record]], [[Encapsulation]]

---

A **POJO** is a simple Java class that adheres to standard object conventions. It is designed to be lightweight and portable, operating without external library dependencies, special restrictions, or framework-specific annotations.

---

### Core Purpose and Evolution

POJOs are built for simplicity. They primarily serve to **encapsulate data and related behavior**, allowing for easy data transfer to functional classes. While POJOs remain a fundamental concept, modern Java has introduced the **Record** as a more concise and specialized alternative for data-centric classes.

---

### Key Characteristics

- **Encapsulation:** Utilizes private instance fields to protect data.
    
- **Standard Accessors:** Provides public getters and setters to interact with fields.
    
- **Standard Methods:** May include constructors, `toString()`, `equals()`, and `hashCode()`.
    
- **Independence:** Does not extend or implement specialized framework-specific classes or interfaces.

---

### Implementation Example

```
public class Person {
    private String name;
    private int age;

    public Person() {}

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() { return name; }
    public void setName(String name) { this.name = name; }

    public int getAge() { return age; }
    public void setAge(int age) { this.age = age; }

    @Override
    public String toString() {
        return "Person{name='" + name + "', age=" + age + "}";
    }
}
```