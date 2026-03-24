---
tags:
  - "#java"
  - "#java_core"
  - OOP
  - principle
  - abstraction
---
# Abstraction

**Related notes:** [[Abstract_Class]], [[Interface]], [[Abstract_Method]]

---

**Abstraction** is the conceptual process of hiding complex implementation details while exposing only the essential features of an object. It allows you to focus on **what** an object does rather than **how** it performs its tasks.

---

### Real-World Analogy

Think of a **TV remote**: you press a "Channel Up" button to change the station. This is the **essential feature** (the "what"). You do not need to understand the internal circuitry, signal frequencies, or infrared protocols (the "how") to successfully use the device.

---

### How Abstraction is Achieved

Java provides two primary mechanisms to implement abstraction, each offering a different "level" of abstraction:

#### 1. Abstract Classes (Partial to Full Abstraction)

- **Abstraction Level:** 0% to 100%.
    
- **Mechanism:** They use the `is-a` relationship.
    
- **Functionality:** They can contain both **abstract methods** (no implementation) and **concrete methods** (with implementation). This allows you to share some common logic while forcing subclasses to define the rest.

#### 2. Interfaces (Full Abstraction)

- **Abstraction Level:** Traditionally 100%.
    
- **Mechanism:** They define a contract of behavior that a class must implement.
    
- **Evolution:** Since Java 8, interfaces can include `default` and `static` methods, providing a way to add implementation while maintaining the interface structure.

---

### Key Characteristics

|**Feature**|**Description**|
|---|---|
|**Complexity Reduction**|By hiding unnecessary details, the system becomes easier to understand and manage.|
|**Reusability**|Standardized templates allow different classes to use the same abstract structure.|
|**No Direct Instantiation**|You **cannot** create an object directly from an `abstract class` or an `interface`. They must be extended or implemented by a concrete class.|
|**Security**|Only the necessary components are exposed to the user, protecting the internal integrity of the application.|

---

### Why Use Abstraction?

- **Maintainability:** You can change the "how" (internal code) without breaking the "what" (how other parts of the program interact with it).
    
- **Decoupling:** It separates the system's design from its implementation, making the code more modular.