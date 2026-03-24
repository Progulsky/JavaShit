---
tags:
  - "#java"
  - "#java_core"
  - platform_structure
---
# jShell

**Related notes:** [[JDK]]

---

**jShell** is an interactive Command Line Interface (CLI) tool introduced in Java 9 as part of the **JDK**. It is a **REPL** (Read-Eval-Print Loop), which fundamentally changed how Java developers learn the language and test ideas. Before jShell, even a simple `System.out.println("Hello")` required a class, a `main` method, and a compilation step. With jShell, you just type the code and hit Enter.

---

### The REPL Cycle

The power of jShell lies in its four-stage loop:

1. **Read:** It takes your Java code or command.
    
2. **Eval:** It evaluates the logic immediately.
    
3. **Print:** It shows you the result (even for expressions that don't explicitly print).
    
4. **Loop:** It waits for your next instruction while keeping previous variables in memory.

---

### Essential Commands

Commands in jShell always start with a **forward slash (`/`)** to distinguish them from Java code.

|**Command**|**Action**|
|---|---|
|**`/help`**|Displays a menu of all available commands.|
|**`/list`**|Shows all snippets you've entered in the current session.|
|**`/vars`**|Lists all variables currently declared and their values.|
|**`/methods`**|Lists all methods you have defined during the session.|
|**`/save [file]`**|Saves your current session's snippets to a `.jsh` file.|
|**`/open [file]`**|Loads and executes snippets from a previously saved file.|
|**`/reset`**|Clears the state (variables/classes) without restarting the tool.|
|**`/exit`**|Safely closes the jShell environment.|

---

### Quality of Life Features

jShell isn't just a basic prompt; it includes several "hidden" features that make it feel like a modern development environment:

- **Implicit Variables:** If you type an expression without assigning it to a variable (e.g., `5 + 10`), jShell automatically creates a variable like `$1` to store the result so you can use it later.
    
- **Forward References:** You can define a method that calls another method that doesn't exist _yet_. jShell will simply warn you and let it work once you eventually define that missing piece.
    
- **Tab Completion:** Pressing `Tab` will autocomplete class names, methods, and variables, just like an IDE.
    
- **Readability:** It supports Java features like **numeric underscores** (`1_000_000`) and standard **comments** (`//`).
    
- **History**: It allows you to scroll through used commands using up/ down arrows
    
- **Code blocks**: you can define code blocks using curly braces `{}`

---

### Why Use It?

- **Rapid Prototyping:** Want to see how `String.split()` handles a specific regex? Don't start a project—just test it in jShell.
    
- **Learning:** It's the best way for beginners to understand loops, logic, and the Java API without the overhead of "Boilerplate" code.
    
- **API Exploration:** Quickly check the return types or behavior of new library methods.

> **Wit & Wisdom:** jShell is like a "scratchpad" for your brain. It's the perfect place to make mistakes because a "reset" is only six characters away.

---

More about jShell ([here]((https://docs.oracle.com/en/java/javase/17/jshell/introduction-jshell.html#GUID-630F27C8-1195-4989-9F6B-2C51D46F52C8)))