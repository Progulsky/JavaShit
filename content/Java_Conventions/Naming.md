---
tags:
  - "#java"
  - "#java_core"
  - convention
---
# Naming

**Related notes:** [[Class]], [[Method]], [[Variable]], [[Package]], [[Generic]], [[Constant]], [[Enum]], [[Boolean]]

---

**Naming conventions** are a set of community-accepted best practices used to name code elements like classes, variables, and methods. While the Java compiler won't stop you from using "bad" names (as long as they are syntactically valid), following these rules is critical for making your code readable and maintainable by other developers.

---

### Core Naming Styles

|**Style**|**Description**|**Example**|
|---|---|---|
|**PascalCase**|Every word starts with a capital letter.|`AccountManager`|
|**camelCase**|First word is lowercase; subsequent words are capitalized.|`calculateTotalValue`|
|**SCREAMING_SNAKE**|All uppercase with underscores between words.|`MAX_RETRY_ATTEMPTS`|

---

### Standard Java Rules

#### 1. Project and Classes (**PascalCase**)

Classes and Interfaces should be **nouns** that describe what the object _is_.

- **Example:** `Scanner`, `ArrayList`, `CustomerService`.

#### 2. Methods and Variables (**camelCase**)

- **Methods:** Should be **verbs** or verb phrases describing an action.
    
    - **Example:** `sendMessage()`, `printReport()`.
        
- **Variables:** Should be descriptive nouns. Avoid single letters except in loops.
    
    - **Example:** `userEmail`, `retryCount`.

#### 3. Packages (**Lowercase & Dot-separated**)

Package names are always lowercase to avoid conflicts with class names. They typically follow a reverse-domain name pattern.

- **Example:** `com.google.search`, `org.apache.commons`.

#### 4. Constants & Enums (**SCREAMING_SNAKE_CASE**)

Used for `static final` fields whose values never change.

- **Example:** `DEFAULT_TIMEOUT`, `MIN_AGE`.

#### 5. Booleans (**is/has/can prefixes**)

Naming booleans as a question makes `if` statements read like English sentences.

- **Example:** `if (isLoggedIn)`, `if (hasPermission)`.

---

### Generics Naming Conventions

When using **Generics**, Java developers use single uppercase letters to keep the type parameter distinct from actual class names.

- **`T`**: Type (Generic placeholder)
    
- **`E`**: Element (used extensively by the Collections framework)
    
- **`K`**: Key (used in Maps)
    
- **`V`**: Value (used in Maps)
    
- **`N`**: Number
    
- **`S, U, V`**: Used when you have multiple generic parameters in one class.

---

### FQCN (Fully Qualified Class Name)

The **FQCN** is the complete "address" of a class. It is the package name followed by the class name. This is how the JVM distinguishes between two classes that have the same name but live in different packages.

- **Simple Name:** `Scanner`
    
- **FQCN:** `java.util.Scanner`

---

All of rules from Google [here](https://google.github.io/styleguide/javaguide)