---
tags:
  - "#java"
  - "#java_core"
  - fundamentals
  - type_system
---
# Casting

**Related notes:** [[Variable]], [[Operator]], [[Inheritance]], [[Polymorphism]]

---

**Casting** is an operator used to explicitly convert one data type into another. It acts as a set of instructions to the compiler, saying, "I know what I'm doing; treat this value as this specific type."

---

### Primitive Casting

Primitive casting is categorized into two types: **Widening** (Automatic) and **Narrowing** (Manual).

- **Widening (Implicit):** Converting a smaller type to a larger type (e.g., `int` to `double`). Java does this automatically because there is no risk of data loss.
    
- **Narrowing (Explicit):** Converting a larger or more precise type to a smaller one (e.g., `double` to `int`). This requires the casting operator `(type)` because it may result in data loss (truncation).

#### Syntax and Arithmetic

> `targetType variable = (targetType) valueOrExpression;`

```
double pi = 3.14;
int roundedPi = (int) pi; // Results in 3 (fractional part is lost)

int var1 = 128;
byte var2 = (byte) (var1 / 2); // Parentheses ensure the result of division is cast
```

---

### Object Casting (OOP)

In Object-Oriented Programming, casting allows you to navigate the **inheritance hierarchy**. It doesn't actually change the object itself; it only changes the **reference type** used to access it.

#### 1. Upcasting (Always Safe)

Upcasting is assigning a subclass object to a superclass reference. Java performs this automatically.

- **Purpose:** Allows for polymorphism (treating different objects as a general type).
    
- **Limitation:** You lose access to subclass-specific methods.

```
Animal a = new Dog(); // Upcasting
a.speak();            // OK: Defined in Animal
// a.bark();          // Compile Error: Animal reference doesn't know about 'bark'
```

#### 2. Downcasting (Risky)

Downcasting is casting a superclass reference back to a subclass type. This must be done manually.

- **Purpose:** To regain access to specific behaviors of the subclass.
    
- **Risk:** Throws a `ClassCastException` at runtime if the object is not actually an instance of the target subclass.

```
Dog d = (Dog) a; // Downcasting
d.bark();        // OK: Now we can bark!
```

---

### Safety with `instanceof`

To avoid runtime crashes, you should always verify the object's type before downcasting using the `instanceof` operator.

```
if (a instanceof Dog) {
    Dog d = (Dog) a;
    d.bark();
}
```

> **Pro-Tip:** Modern Java (16+) supports **Pattern Matching for `instanceof`**, which combines the check and the cast into one clean step: `if (a instanceof Dog d) { d.bark(); }`

---

### Why Use Casting?

1. **Access Subclass Logic:** Essential when you have a collection of general types (like a `List<Shape>`) but need to trigger specific logic for a `Circle`.
    
2. **Generic Data Handling:** Often used in frameworks where objects are passed around as `Object` or generic interfaces and need to be refined for specific processing.
    
3. **Arithmetic Precision:** Controls how numbers are handled in complex equations to prevent unintentional rounding or overflow errors.