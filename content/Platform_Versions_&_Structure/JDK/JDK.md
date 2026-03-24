---
tags:
  - "#java"
  - "#java_core"
  - platform_structure
---
# JDK

**Related notes:** [[JVM]], [[jShell]], [[Package]], [[LTS]], [[SE]]

---

The **JDK** is the comprehensive software environment used to develop and run Java applications. Think of it as a complete "builder’s kit." If you want to write a single line of Java code and see it execute, the JDK is the mandatory foundation.

---

### Core Components: What’s Under the Hood?

The JDK is a "super-set" that contains several layers of technology:

1. **The Compiler (`javac`):** This is the heart of the development process. It translates your human-readable `.java` files into platform-independent **Bytecode** (`.class` files).
    
2. **The JVM (Java Virtual Machine):** This is the engine that actually executes the bytecode. It allows Java to follow the "Write Once, Run Anywhere" (WORA) philosophy.
    
3. **Standard Class Libraries (API):** A massive collection of pre-written code (like `java.util` for collections or `java.time` for dates) that saves you from reinventing the wheel.
    
4. **Development Tools:**
    
    - **`jShell`:** A REPL tool for running snippets of code without creating a full class.
        
    - **`javadoc`:** Generates HTML documentation directly from your code comments.
        
    - **`jar`:** Packages your classes and resources into a single executable file.
        
    - **`jdb`:** The command-line debugger.

---

### The Evolution: JDK vs. JRE

In the past, you might have heard of the **JRE (Java Runtime Environment)**.

- **JRE:** Was for _running_ Java (contained the JVM + Libraries).
    
- **JDK:** Was for _developing_ Java (contained the JRE + Tools).

> **Note:** Starting with **Java 11**, the JRE is no longer offered as a separate download. Modern developers and users alike simply use the JDK or a custom "slimmed-down" runtime created with tools like `jlink`.