---
tags:
  - "#java"
  - "#java_core"
  - fundamentals
  - syntax
---
# Operator

**Related notes:** [[Expression]], [[Literal]], [[Variable]], [[Token]]

---

An **operator** is a symbol or **keyword** used to perform operations on **operands**, such as **variables**, **literals**, and **expressions**.

---

### Operator Groups

| **Category**   | **Operators & Descriptions**                                                                                          |
| -------------- | --------------------------------------------------------------------------------------------------------------------- |
| **Arithmetic** | Used for mathematical calculations.                                                                                   |
| **Relational** | `==` (equal to), `!=` (not equal), `>` (greater than), `<` (less than), `>=` (greater or equal), `<=` (less or equal) |
| **Logical**    | `&&` (logical AND (also shortcuit)), `\|\|` (logical OR (also shortcuit)), `!` (logical NOT)                          |
| **Assignment** | `=` (assign), `+=` (add and assign), `-=` (subtract and assign)                                                       |
| **Unary**      | `++` (increment), `--` (decrement), `+` (positive sign), `-` (negative sign), `!` (logical NOT)                       |
| **Bitwise**    | `&` (AND), `\|` (OR), `^` (XOR), `~` (NOT), `<<` (left shift), `>>` (right shift)                                     |
| **Ternary**    | `operand1 ? operand2 : operand3` (Short form of if-statement)                                                         |
| **Other**      | Casting, `instanceof`, Diamond operator (`<>`)                                                                        |

---

### Operator Priority

To check the precedence (priority) of these operators, you can refer to the following resource:

[Java Precedence Guide](https://introcs.cs.princeton.edu/java/11precedence/)
