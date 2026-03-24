---
tags:
  - "#java"
  - "#java_core"
  - OOP
  - method
---
# Varargs

**Related notes:** [[Method]], [[Array]]

---

**Varargs** (variable arguments) allow a method to accept an unspecified number of arguments. Instead of forcing the caller to manually pack values into an array, you use the ellipsis (`...`) syntax to make the method more flexible and concise.

---

### Implementation and Usage

Inside the method, the varargs parameter is treated exactly like an **array**. This allows you to iterate through the arguments using a standard loop or an enhanced `for-each` loop.

```
public void printNumbers(int... numbers) {
    // 'numbers' is treated as an int[] array here
    for (int num : numbers) {
        System.out.println(num);
    }
}
```

#### Flexibility in Calling

Varargs methods are highly versatile. You can call them with any number of arguments, or even none at all:

```
printNumbers(1, 2, 3);            // Passed as 3 arguments
printNumbers(10, 20, 30, 40, 50); // Passed as 5 arguments
printNumbers();                   // Passed as an empty array
int[] myNums = {7, 8, 9};
printNumbers(myNums);             // You can still pass a literal array
```

---

### Strict Rules for Varargs

To prevent ambiguity during compilation, Java enforces two specific rules:

1. **The "Last Place" Rule:** The varargs parameter must always be the **final parameter** in the method signature.
    
2. **The "Only One" Rule:** A method can have **at most one** varargs parameter.

```
// VALID
void doSomething(String label, int... values) {}

// INVALID: Varargs must be last
// void doSomething(int... values, String label) {}

// INVALID: Only one varargs allowed
// void doSomething(int... nums, String... names) {}
```

---

### Varargs vs. Standard Arrays

Choosing between `Type...` and `Type[]` depends on how you expect the method to be used:

|**Feature**|**Varargs (String... names)**|**Array (String[] names)**|
|---|---|---|
|**Call Style**|`greet("Alice", "Bob")`|`greet(new String[]{"Alice", "Bob"})`|
|**No Arguments**|`greet()` (Valid)|`greet(new String[]{})` (Requires empty array)|
|**Best For**|Ad-hoc lists of items or utility methods.|Situations where the data is already stored in an array.|
