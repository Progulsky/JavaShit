---
tags:
  - "#java"
  - "#java_core"
  - project
---
# Package

**Related notes:** [[Class]], [[JDK]]

---

A **package** is a mechanism used in Java to group related classes, interfaces, and sub-packages. Conceptually, you can think of it like a folder system on your computer that organizes your files. Using a hierarchical structure (like `com.company.project.module`), packages help manage large-scale software projects.

---

### Why Use Packages?

- **Organization:** Keeps thousands of classes manageable by grouping them by functionality (e.g., `ui`, `util`, `database`).
    
- **Namespace Management:** Allows two classes to have the same name (e.g., `java.util.List` and `java.awt.List`) as long as they live in different packages.
    
- **Access Control:** Java provides a "package-private" access level (the default). Classes with this level can only be seen by other classes in the same package.
    
- **Code Reusability:** Well-organized packages make it easier to export a "library" of code for use in other projects.

---

### The `package` Statement

The `package` statement declares which namespace a class belongs to.

- **Rule 1:** It **must** be the very first line of code in your file (after comments).
    
- **Rule 2:** The package name must exactly match the directory structure on your disk. If your class is in `src/com/shop/orders/`, the statement must be:

```
package com.shop.orders;

public class OrderManager { ... }
```

---

### Accessing Classes: Imports vs. FQCN

There are two ways to use a class that lives in a different package:

#### 1. The `import` Keyword

This is the most common method. It tells the compiler where to find the class so you can use its short name.

- **Specific Import:** `import java.util.Scanner;` (Preferred for clarity).
    
- **Wildcard Import:** `import java.util.*;` (Imports all classes in that package, but **not** sub-packages).

#### 2. Fully Qualified Class Name (FQCN)

If you don't want to import a class, or if you have two classes with the same name from different packages, you must use the FQCN.

```
// Using FQCN to resolve a conflict
java.util.Date utilDate = new java.util.Date();
java.sql.Date sqlDate = new java.sql.Date(12345L);
```

---

### Static Imports

A specialized version of the import statement allows you to import **static members** (methods or constants) of a class so you can use them without the class name prefix.

```
import static java.lang.Math.PI;
import static java.lang.Math.sqrt;

// Now you can use them directly
double area = PI * sqrt(16); 
```

---

### Standard Java Packages

Java comes with a massive library of built-in packages. Here are the heavy hitters:

|**Package**|**Purpose**|
|---|---|
|**`java.lang`**|Fundamental classes (String, Math, Object). **Automatically imported** into every file.|
|**`java.util`**|Collections, Scanner, Date, and Random.|
|**`java.io`**|Classes for system input and output through data streams.|
|**`java.net`**|Classes for implementing networking applications.|

> **AI Tip:** Always try to use specific imports instead of wildcards (`*`). It makes it much easier for other developers (and your IDE) to figure out exactly which class your code is using, preventing "shadowing" bugs where two packages contain classes with the same name.