---
tags:
  - "#java"
  - "#java_core"
  - class
---
# Random

**Related notes:** [[Class]]

---

The `java.util.Random` class is the standard utility for generating **pseudo-random** numbers. It’s called "pseudo" because the numbers aren't truly random; they are calculated using a mathematical formula based on a starting value called a **seed**.

---

### Implementation Basics

To start generating numbers, you need to import the class and create an instance of the generator.

```
import java.util.Random;

Random rand = new Random(); // Uses the current time as a default seed
```

---

### Essential Methods

|**Method**|**Range**|**Description**|
|---|---|---|
|**`nextInt()`**|$-2^{31}$ to $2^{31}-1$|Returns any valid `int` (negative or positive).|
|**`nextInt(int bound)`**|$0$ to `bound - 1`|**Most Common:** Generates an integer within a specific range.|
|**`nextDouble()`**|$0.0$ to $1.0$|Returns a `double` (exclusive of 1.0).|
|**`nextBoolean()`**|`true` / `false`|A virtual "coin flip."|

---

### Seeding: The Secret to Repeatability

If you create two `Random` objects with the exact same seed, they will generate the **exact same sequence** of numbers. This is incredibly useful for:

- **Debugging:** Reproducing a specific random bug.
    
- **Gaming:** Generating the same map layout for every player using a "Map Seed."

```
Random rand1 = new Random(42);
Random rand2 = new Random(42);

System.out.println(rand1.nextInt(100)); // Say it's 30
System.out.println(rand2.nextInt(100)); // It will definitely be 30
```

---

### Random vs. Math.random()

While you might have used `Math.random()` before, using the `Random` class is generally preferred for several reasons:

- **Flexibility:** `Math.random()` only gives you doubles. `Random` handles `int`, `long`, `boolean`, and `float` directly.
    
- **Control:** You can't seed `Math.random()`.
    
- **Efficiency:** If you need many random numbers, reusing a `Random` instance is slightly faster than calling the static `Math.random()` method repeatedly.

> **Wit & Wisdom:** Don't use `java.util.Random` for anything involving actual security (like generating passwords). Because it's predictable, a clever person could figure out your "random" sequence. For security, use **`java.security.SecureRandom`** instead.