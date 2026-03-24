---
tags:
  - "#java"
  - "#java_core"
  - fundamentals
  - metadata
---
# Annotation

**Related notes:** [[Token]], [[Class]], [[Interface]], [[Method]]

---

**Annotations** are a specialized form of **metadata** used to provide supplemental information about a program. They formally describe additional data about the code without being part of the program logic itself.

---
### **Annotations vs. Comments**

While both provide info about code, they differ significantly:

- **Comments:** Purely for human readers; ignored by the compiler.
    
- **Annotations:** Structured and machine-readable. They can be processed by the **compiler**, deployment tools, or at **runtime** using reflection.

> **Key Rule:** Annotations do not directly affect the execution of the code they annotate, but they can influence how tools and frameworks treat the code.

---

## Common Built-in Annotations

Java provides several standard annotations used to communicate with the compiler:

- **`@Override`**: Checks that a method is correctly overriding a method from a superclass. If the method signature doesn't match, the compiler throws an error.
    
- **`@Deprecated`**: Marks a program element (class, method, field) as obsolete. Using it triggers a compiler warning.
    
- **`@SuppressWarnings`**: Tells the compiler to ignore specific warnings (like "unused variables") within the annotated block.

```
public class Example {
    @Override
    public String toString() {
        return "Annotation Example";
    }

    @Deprecated
    public void oldMethod() {
        // This method is outdated
    }
}
```