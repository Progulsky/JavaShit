---
tags:
  - "#java"
  - "#java_core"
  - class
  - class_subtype
  - nested
---
# Inner_Class

**Related notes:** [[Class]], [[Static_Nested_Class]], [[Local_Class]], [[Anonymous_Class]]

---

In Java, an **Inner Class** refers specifically to a non-static nested class. It is treated like an instance member — similar to a field or a method — meaning it belongs to a specific **instance** of the outer class.

---

### The Mandatory Instance Link

The defining rule for a member inner class is its dependency: it **cannot exist** without an instance of the outer class.

---

### How to Instantiate

- **From within the Outer Class:** You can instantiate it normally, just like any other object.
    
- **From outside the Outer Class:** You must first create an instance of the outer class, then use the specialized `new` syntax.

```
Outer outer = new Outer();
Outer.Inner inner = outer.new Inner();

// Alternatively, using the 'var' keyword:
var inner = new Outer().new Inner();
```

---

### Access Rules

- **Access to Outer:** The inner class has direct access to **all** members of its outer class, including private fields and methods.
    
- **Bidirectional Privacy:** The outer class can also access the **private** members of the inner class, provided it does so through an inner class instance.
    
- **Static Members:** Traditionally, inner classes could not declare static members. However, since **Java 16**, this restriction has been relaxed, allowing inner classes to contain static methods and fields.

---

### Handling Naming Conflicts (Shadowing)

If an inner class defines a variable with the same name as one in the outer class, you can resolve the conflict using the **qualified `this`** syntax.

```
public class House {
    private String color = "Blue";

    class Room {
        private String color = "White";

        void printColors() {
            // Refers to the Room's color
            System.out.println("Room color: " + this.color);       
            
            // Refers to the House's color
            System.out.println("House color: " + House.this.color); 
        }
    }
}
```

---

### The Downside: Memory Leaks

Every instance of a member inner class maintains a "hidden" strong reference to the outer class object. This prevents the outer object from being **garbage collected** as long as the inner object is still in use.

> **Note:** If you pass an inner class object (such as a listener or task) to a long-lived part of your program, you may accidentally keep the entire outer object "trapped" in memory, leading to a memory leak.