---
tags:
  - "#java"
  - "#java_core"
  - generic
  - class
  - class_subtype
---
# Generic_Class

**Related notes:** [[Class]], [[Generic]], [[Generalization]], [[Generic_Method]], [[Type_Parameter]], [[Type_Argument]]

---

A **Generic Class** is a class that includes a **Type Parameter**, allowing it to operate on different data types while maintaining strict compile-time type safety. Instead of writing separate classes for `String`, `Integer`, or custom objects, you write one generic class that adapts to the type you provide.

---

### Syntax and Implementation

In a generic class, the type parameter (conventionally `T`) acts as a placeholder. When you instantiate the object, you replace this placeholder with a concrete class.

```
class Box<T> {
    private T value; // T stands for "Type"

    public void setValue(T value) {
        this.value = value;
    }

    public T getValue() {
        return value;
    }
}

// Usage with String
Box<String> stringBox = new Box<>();
stringBox.setValue("Hello");

// Usage with Integer
Box<Integer> intBox = new Box<>();
intBox.setValue(123);
```

#### Multiple Type Parameters

You are not limited to one type. For instance, a **Map-like** structure uses two parameters, typically `K` for Key and `V` for Value.

```
class Pair<K, V> {
    private K key;
    private V value;

    public Pair(K key, V value) {
        this.key = key;
        this.value = value;
    }

    public K getKey() { return key; }
    public V getValue() { return value; }
}

Pair<String, Integer> student = new Pair<>("Alice", 20);
```

---

### Bounded Type Parameters

By default, a type parameter `T` can be any object. However, you can use **bounds** to restrict the types that can be used with your generic class.

#### 1. Upper Bounds (`extends`)

An upper bound restricts `T` to be a specific class or its subclasses (or an interface and its implementers). This allows you to call methods defined in the bounding class inside your generic class.

```
// T must be Number or a subclass (Integer, Double, etc.)
class NumberBox<T extends Number> {
    private T num;

    public NumberBox(T num) {
        this.num = num;
    }

    public double doubleValue() {
        return num.doubleValue(); // Safe to call because T is guaranteed to be a Number
    }
}
```

#### 2. Multiple Bounds

You can enforce that a type parameter meets multiple requirements using the `&` operator.

> **Important Rules:**
> - You can only extend **one class** (it must be listed first).
> - You can implement **any number of interfaces**.

```
class MyClass<T extends Number & Comparable<T> & Serializable> {
    // T must be a Number AND implement both interfaces
}
```