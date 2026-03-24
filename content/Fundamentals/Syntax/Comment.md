---
tags:
  - "#java"
  - "#java_core"
  - fundamentals
  - syntax
  - documentation
---
# Comment

**Related notes:** [[Token]]

---

Java provides two primary types of comments used for internal notes and debugging. These are technically **lexical elements** that the compiler ignores during the conversion of source code into bytecode.

---

## Implementation Comment Types

|**Type**|**Syntax**|**Description**|
|---|---|---|
|**Single-line**|`// comment`|Extends from the `//` symbol to the **end of the current line**. Ideal for short notes or disabling a single line of code.|
|**Multi-line**|`/* comment */`|Also known as **Block Comments**. Everything between `/*` and `*/` is ignored. Useful for long explanations or disabling large blocks of code.|

---

## Core Use Cases

#### 1. Explaining the "Why"

Good comments focus on the **rationale** behind a decision rather than just stating what the code does (since the code itself should be readable).

```
// Using a stable sort here because order of equal elements must be preserved
Collections.sort(userList); 
```

#### 2. Debugging ("Commenting Out")

During development, you can use comments to prevent specific code from executing without deleting it.

```
// System.out.println("Temporary debug message"); 
int result = calculateValue();
```

#### 3. Marking Tasks (TODOs)

Many IDEs recognize the `TODO` keyword inside a comment and will highlight it in a dedicated window.

```
// TODO: Refactor this method to improve performance after the API update
public void processData() { ... }
```

---

### Crucial Syntax Rules

- **No Nesting:** You cannot put a multi-line comment inside another multi-line comment. This will cause a compilation error because the first `*/` encountered will close the entire comment.

```
     /* This is okay. 
       // This single-line comment inside a block is also okay.
    */
    
    /* /* This will cause an ERROR */ 
       The compiler thinks the comment ended at the first asterisk-slash.
    */ 
```

- **Lexical Treatment:** Comments are stripped out during the early stages of compilation. They have **zero impact** on the performance or size of your final `.class` file.
