---
tags:
  - "#java"
  - "#java_core"
  - class
  - class_subtype
  - nested
---
# Local_Class

**Related notes:** [[Class]], [[Inner_Class]], [[Static_Nested_Class]], [[Anonymous_Class]], [[Code_Block]], [[Method]]

---

In Java, a **local class** is a class defined inside a block — typically within the body of a method. These are a specialized type of inner class used when a class is needed for a very specific, narrow purpose that does not require visibility elsewhere.

---

### Implementation Example

In this example, `TaxCalculator` is encapsulated within the `processOrder` method, allowing it to use local data to perform contextual logic.

```
public class CheckoutManager {
    private double basePrice = 100.0;

    public void processOrder(String regionCode) {
        // A local variable in the method
        double regionalDiscount = 5.0; 

        // Local Class definition
        class TaxCalculator {
            double calculateTotal() {
                double taxRate;
                
                // Logic specific to this method's context
                if (regionCode.equals("EU")) {
                    taxRate = 0.20;
                } else {
                    taxRate = 0.08;
                }

                // Accessing:
                // 1. Private member of outer class (basePrice)
                // 2. Local variable of method (regionalDiscount)
                return (basePrice - regionalDiscount) * (1 + taxRate);
            }
        }

        // Using the local class
        TaxCalculator calc = new TaxCalculator();
        System.out.println("Total Price for " + regionCode + ": $" + calc.calculateTotal());
    }
}
```

---

### Key Characteristics

- **Restricted Scope:** They are only visible and accessible within the specific block where they are declared.
    
- **Variable Access:** They can access all members of the enclosing class. They can also access **local variables** of the enclosing block, provided those variables are `final` or **effectively final** (the value remains unchanged after initialization).
    
- **No Static Members:** Since they are associated with an instance of the enclosing class, they cannot define static fields or methods (excluding constant variables).
    
- **No Access Modifiers:** You cannot use `public`, `private`, or `protected`. They are local to the block, behaving like a local variable.

---

### Why only Final or Effectively Final?

This requirement exists due to a mismatch in memory lifetimes. Local variables live on the **Stack** and are destroyed when the method ends, while class instances live on the **Heap** and may survive longer.

To bridge this gap, the compiler "captures" the variable by creating a hidden copy inside the class instance. If the original variable were allowed to change after this copy was made, the two values would fall out of sync. Java enforces finality to ensure the captured copy always accurately reflects the original value.

---

### Benefits of Local Classes

1. **Strict Encapsulation:** Hides classes used only by a single method, reducing "namespace clutter."
    
2. **Logic Organization:** Keeps the class definition immediately adjacent to the code that uses it, making small tasks easier to follow.
    
3. **Environment Capturing:** Excellent for capturing the state of a method's execution to perform tasks later, a pattern often seen in GUI event listeners or legacy threading.