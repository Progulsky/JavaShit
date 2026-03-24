---
tags:
  - "#java"
  - "#java_core"
  - error
---
# Exception

**Related notes:** [[Code_Block]], [[Scope]], [[Class]]

---

An **exception** is an unwanted or unexpected event that occurs during the execution of a program (at runtime) and disrupts the normal flow of the program's instructions. In Java, exceptions are objects that encapsulate information about the error.

---

### The Exception Hierarchy

All exception types are subclasses of the built-in class `Throwable`.

- **Error:** Indicates serious problems that a reasonable application should not try to catch (e.g., `OutOfMemoryError`, `StackOverflowError`). These are usually external to the application's control.
    
- **Exception:** The main class for errors that a program should handle.
    
    - **Checked Exceptions:** Verified at **compile-time**. The compiler requires you to either handle them with `try-catch` or declare them using the `throws` keyword (e.g., `IOException`, `SQLException`).
        
    - **Unchecked Exceptions (RuntimeExceptions):** Not checked at compile-time. They usually occur due to logic flaws, such as `NullPointerException` or `ArithmeticException`.

---

### Handling Exceptions: Try, Catch, and Finally

Java provides a structured way to handle errors using specific blocks of code. Each block has its own **scope**.

#### 1. The `try` Block

Contains the code that might throw an exception. If an error occurs, execution of the `try` block stops immediately, and control moves to the `catch` block.

#### 2. The `catch` Block

Used to handle the exception. You must declare a **variable** (e.g., `Exception e`) to hold the exception object. You can have multiple `catch` blocks to handle different types of exceptions separately.

#### 3. The `finally` Block

An **optional** block that executes **regardless** of whether an exception was thrown or caught. It is typically used for cleanup tasks, like closing file streams or database connections.

```
try {
    int[] nums = {1, 2, 3};
    System.out.println(nums[10]); // Throws exception
} catch (ArrayIndexOutOfBoundsException e) {
    System.out.println("Caught an error: " + e.getMessage());
} finally {
    System.out.println("Cleanup: This block always executes.");
}
```

---

### Keywords: `throw` vs `throws`

- **`throw`:** Used to manually trigger an exception.

```
    if (age < 18) {
        throw new IllegalArgumentException("Access Denied");
    }
```

- **`throws`:** Used in a method signature to signal that this method might "pass the buck" and throw an exception to the caller.

```
    public void readFile() throws IOException { ... }
```

---

### Custom Exceptions

You can create your own exception classes by extending `Exception` (for checked) or `RuntimeException` (for unchecked). This is useful for representing business-logic errors specific to your application.

```
class InsufficientFundsException extends Exception {
    public InsufficientFundsException(String message) {
        super(message);
    }
}
```

> **AI Insight:** While it’s tempting to catch the general `Exception` class, it is a best practice to catch specific exceptions. This prevents your code from accidentally "swallowing" serious errors that you didn't intend to handle.

---

All of exceptions [here](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/Exception.html)