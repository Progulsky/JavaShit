---
tags:
  - "#java"
  - "#java_core"
  - I/O
  - input
---
# Input

**Related notes:** [[Class]], [[Output]]

---

Reading user input is a fundamental part of interactive programming. Java offers several ways to capture data from the console, ranging from the beginner-friendly `Scanner` class to high-performance byte streams.

---

### 1. The Scanner Class (`java.util.Scanner`)

The **Scanner** is the go-to tool for most developers because it can parse primitive types and strings using regular expressions.

#### Common Methods:

- **`nextLine()`**: Reads an entire line of text (including spaces).
    
- **`next()`**: Reads the next token/word (stops at whitespace).
    
- **`nextInt()`, `nextDouble()`, `nextBoolean()`**: Read and automatically convert input into specific types.

> **The "Scanner Bug":** When you use `nextInt()` followed by `nextLine()`, the `nextLine()` often appears to be skipped. This happens because `nextInt()` leaves a "newline" character (`\n`) in the buffer.
> 
> **The Fix:** Add an extra `scanner.nextLine();` immediately after your `nextInt()` to "flush" the buffer.

---

### 2. High-Performance Input: BufferedReader

For applications processing massive amounts of data, `BufferedReader` is significantly faster than `Scanner` because it buffers characters for efficient reading.

```
import java.io.BufferedReader;
import java.io.InputStreamReader;

BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
String input = reader.readLine(); // Returns a String; must be parsed manually
```

---

### 3. Secure Input: System.console()

If you are writing a terminal application that requires passwords, `System.console()` is the preferred choice. It provides a `readPassword()` method that masks input.

> **Note:** This often returns `null` in IDE consoles (like IntelliJ or Eclipse). It is designed for use in a real system terminal/command prompt.

---

### 4. Low-Level Streams

|**Method**|**Description**|
|---|---|
|**`System.in`**|The raw "Standard Input" stream. It reads data as **bytes**.|
|**`InputStreamReader`**|A bridge that decodes bytes into **characters**.|
|**`DataInputStream`**|Used for reading machine-independent primitive data types from a binary stream.|

---

### 5. Command-Line Arguments

Sometimes input is provided _before_ the program starts. These values are stored in the `String[] args` array within the `main` method.

```
// Run as: java MyApp Alice 25
public static void main(String[] args) {
    String name = args[0]; // Alice
    String age = args[1];  // 25
}
```

---

### Comparison Summary

|**Tool**|**Ease of Use**|**Performance**|**Best For**|
|---|---|---|---|
|**Scanner**|⭐⭐⭐⭐⭐|⭐⭐|Basic console apps and parsing types.|
|**BufferedReader**|⭐⭐|⭐⭐⭐⭐⭐|Reading large text files or fast competitive programming.|
|**Console**|⭐⭐⭐|⭐⭐⭐|Secure password entry in real terminals.|
|**Args[]**|⭐⭐⭐⭐|⭐⭐⭐⭐⭐|Passing configuration/flags at startup.|