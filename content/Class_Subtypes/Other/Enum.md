---
tags:
  - "#java"
  - "#java_core"
  - class
  - class_subtype
  - immutability
---
# Enum

**Related notes:** [[Class]], [[Constant]]

---

An **Enum** is a specialized data type used to define a collection of named constant values. It is ideal for scenarios where you have a fixed, predefined set of options, such as days of the week, compass directions, or application states.

---

### Implementation Example

Using an Enum ensures that only valid transaction types can be passed to your methods, providing a robust alternative to using arbitrary strings or integers.

```
public enum TransactionType {
    DEPOSIT,
    WITHDRAW,
    TRANSFER,
    BALANCE_CHECK
}

public static void handleTransaction(TransactionType type) {
    switch (type) {
        case DEPOSIT -> System.out.println("Processing a deposit...");
        case WITHDRAW -> System.out.println("Processing a withdrawal...");
        case TRANSFER -> System.out.println("Processing a transfer...");
        case BALANCE_CHECK -> System.out.println("Checking account balance...");
        default -> System.out.println("Unknown transaction type.");
    }
}
```

---

### Key Characteristics

- **Class-Based:** Under the hood, Enums are specialized classes. Every enum constant is an instance of that enum type.
    
- **Type Safety:** You cannot assign a value outside of the defined constants, preventing logic errors.
    
- **Rich Functionality:** Unlike simple constants, Enums can contain **fields**, **methods**, and **constructors**.
    
- **Switch Integration:** They work seamlessly with switch expressions and statements for clean control flow.

---

### Why Use Enums?

1. **Safety:** Prevents invalid values from entering your system.
    
2. **Readability:** Replaces cryptic "magic numbers" or strings with descriptive names.
    
3. **Encapsulation:** Allows you to attach specific logic or data (like a transaction fee) directly to a constant.

---

### Limitations

- **Not for Dynamic Data:** Enums are for fixed sets known at compile time. They should not be used for values that change frequently or are loaded from external sources like databases or user input.
    
- **Not Just Integers:** While they have an order, Enums are full objects, making them much more powerful and safer than `static final int` constants.

---

### Built-in Helper Methods

Java provides several standard methods for working with Enum constants:

|**Method**|**Description**|
|---|---|
|`values()`|Returns an array containing all constants in the order they are declared.|
|`name()`|Returns the exact name of the constant as a String.|
|`ordinal()`|Returns the numerical position of the constant (starting at 0).|
|`valueOf(String)`|Converts a String that matches a constant name into the actual Enum object.|