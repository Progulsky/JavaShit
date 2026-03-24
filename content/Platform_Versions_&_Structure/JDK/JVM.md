---
tags:
  - "#java"
  - "#java_core"
  - platform_structure
---
# JVM

**Related notes:** [[JDK]]

---

The **JVM** is the heart of the Java ecosystem. It is an abstract computing machine that provides a runtime environment in which Java bytecode can be executed. It follows the famous philosophy: **"Write Once, Run Anywhere" (WORA)**. Because the JVM is available for many hardware and software platforms, the same `.class` file can run on Windows, macOS, or Linux without modification.

---

### Key Functions of the JVM

The JVM acts as a middleman between your compiled code and the underlying hardware. Its primary responsibilities include:

1. **Bytecode Execution:** It translates the platform-independent bytecode into instruction sets that the specific host CPU understands.
    
2. **Memory Management:** One of its greatest strengths is **Garbage Collection**, which automatically reclaims memory from objects that are no longer in use, preventing most memory leaks.
    
3. **Security:** It includes a **Bytecode Verifier** and a "sandbox" model to ensure that untrusted code cannot perform malicious actions on your system.
    
4. **Entry Point Detection:** It specifically looks for the `public static void main(String[] args)` (**PSVM**) method to begin program execution.

---

### Internal Architecture

To perform these functions, the JVM is divided into several sophisticated subsystems:

#### 1. Class Loader Subsystem

This component is responsible for loading, linking, and initializing the `.class` files. It loads classes "on-demand" (dynamically) the first time they are referenced during runtime.

#### 2. Runtime Data Areas (Memory)

The JVM divides memory into specific areas to stay organized:

- **Method Area:** Stores class-level data, including static variables and method code.
    
- **Heap:** The "big pool" of memory where all **Objects** and their instance variables are stored. This is where the Garbage Collector does its work.
    
- **Stack:** Stores local variables and partial results. Each thread has its own private stack that lives and dies with the method call.

#### 3. Execution Engine

This is where the actual "work" happens. It contains:

- **Interpreter:** Reads bytecode and executes it line-by-line (faster to start, but slower to run).
    
- **JIT Compiler (Just-In-Time):** Identifies "hot" (frequently used) code and compiles it into native machine code for high-performance execution.
    
- **Garbage Collector (GC):** Periodically scans the heap to delete unreferenced objects.

---

### Why the JVM Wins

The JVM isn't just for Java anymore. Because it executes bytecode, other modern languages like **Kotlin**, **Scala**, and **Groovy** all run on the JVM. This allows these languages to use the massive library of existing Java tools and high-performance memory management.

> **Wit & Wisdom:** The JVM is like a professional translator at the UN. You speak "Java," the computer speaks "Binary," and the JVM ensures that no matter what "room" (OS) you're in, the message is delivered perfectly—and it even cleans up the coffee cups (memory) afterward.