---
tags:
  - "#java"
  - "#java_core"
---
# Perturbation

**Related notes:** 

---

This is one of the smartest micro-optimizations in Java's `HashMap`. To understand why this specific line of code exists, we first need to look at **the problem** it solves: the fact that `HashMap` ignores most of your hash code when calculating bucket indices.

---

### 1. The Problem: "Tunnel Vision"

Java `HashMap` arrays usually start very small (default size is 16). To find which bucket an object goes into, Java uses this index formula:

$$Index = (n - 1) \& hash$$
_(where n is the table size)_

If the table size is **16** (10000​), then n−1 is **15** (0000...1111​). When you perform the bitwise `&` with `1111`, **only the last 4 bits of the hash code matter.**

#### The Scenario

Imagine you have two objects with these 32-bit hash codes. Notice they are very different numbers, but identical in the last 4 bits.

- **Hash A:** `1111 1111 0000 0000 0000 0000 0000 0101` (Large Number)
    
- **Hash B:** `0000 0000 0000 0000 0000 0000 0000 0101` (Small Number)

If we calculate the index for a table of size 16:

- **Index A:** `...0101` & `1111` = **5**
    
- **Index B:** `...0101` & `1111` = **5**

**Result:** A collision. The `HashMap` completely ignored the top 28 bits of information in Hash A.

---

### 2. The Solution: "The Spread"

Since the index calculation only looks at the **Lower Bits**, we need a way to force the **Upper Bits** to influence the Lower Bits. We do this by "folding" the top half of the hash code on top of the bottom half.

#### The Code Breakdown

1. **`h >>> 16`**: This is an unsigned right bit-shift. It takes the top 16 bits of the integer and moves them down to the bottom 16 positions.
    
2. **`^` (XOR)**: This is the Exclusive-OR operator. It combines bits such that if the bits are different, the result is 1. If they are the same, it is 0. XOR is perfect for mixing because it doesn't bias the result toward all 1s (like OR) or all 0s (like AND).

---

### 3. Step-by-Step Visualization

Let's look at **Hash A** again and apply the perturbation.

**Original Hash A (h):** `1111 1111 0000 0000` `0000 0000 0000 0101` _(Top half is all 1s and 0s mixed. Bottom half ends in 0101)_

**Shifted (h>>>16):** `0000 0000 0000 0000` `1111 1111 0000 0000` _(The top half has moved to the bottom)_

**The XOR Operation (h∧(h>>>16)):**

```
  1111 1111 0000 0000 0000 0000 0000 0101  (Original)
^ 0000 0000 0000 0000 1111 1111 0000 0000  (Shifted)
-----------------------------------------
  1111 1111 0000 0000 1111 1111 0000 0101  (New Hash)
```

**Wait, the last 4 bits are still `0101`!** In _this specific_ example, the result didn't change because the bits aligned that way. **However**, let's change just **one bit** in the upper part of the original hash (the 20th bit) to see how it cascades down.

**Modified Hash A:** `0000 0000 0001 0000` `0000 0000 0000 0101`

**Shifted:** `0000 0000 0000 0000` `0000 0000 0001 0000`

**XOR Result:** The `1` from the top half falls down and flips a `0` in the bottom half. The final sequence of bits changes entirely.