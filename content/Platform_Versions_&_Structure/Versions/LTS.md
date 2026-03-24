---
tags:
  - "#java"
  - "#java_core"
  - platform_version
---
# LTS

**Related notes:** [[JDK]], [[SE]]

---

**Long-Term Support (LTS)** is a designation given to specific versions of the **JDK** that are intended for high-stability, long-term use in production environments. Unlike "Feature" releases, which come out every six months and are only supported until the next version arrives, LTS versions receive security patches, bug fixes, and performance updates for many years.

---

### Why LTS Matters

In the world of enterprise software, stability is king. Migrating a massive application to a new Java version every six months is risky and expensive. LTS versions provide a "safe harbor" for developers and businesses.

- **Stability:** LTS releases are the most battle-tested. By the time a version becomes the industry standard, millions of developers have already ironed out its quirks.
    
- **Predictability:** Organizations can plan their infrastructure around an LTS version, knowing it will be supported for at least 5 to 8+ years.
    
- **Security:** Vendors (like Oracle, Amazon, or Azul) prioritize security patches for these versions, ensuring your system stays protected against new vulnerabilities without requiring a major code rewrite.

---

### The LTS Timeline

Java's release cadence changed in 2017. Now, a new version is released every six months (March and September), but an LTS version is designated every two years.

|**Version**|**Status**|**Release Date**|
|---|---|---|
|**Java 8**|**LTS** (Legacy Standard)|2014|
|**Java 11**|**LTS**|2018|
|**Java 17**|**LTS**|2021|
|**Java 21**|**Current LTS Standard**|2023|
|**Java 25**|**Next Planned LTS**|2025 (Projected)|

---

### LTS vs. Non-LTS (Feature Releases)

Think of the relationship between these versions like a smartphone OS or a video game:

- **Non-LTS (e.g., Java 22, 23, 24):** These are like "Beta" or "Feature" updates. They introduce exciting new tools (like Virtual Threads or Pattern Matching) so developers can experiment and give feedback. However, once the _next_ version comes out, the old one stops receiving updates immediately.

- **LTS:** These are the "Final Gold Version." They gather all the successful experiments from the previous non-LTS versions and package them into a single, rock-solid platform.

---

### Which one should you use?

- **For Production/Work:** Always stick with an **LTS** version (currently Java 21 is the professional recommendation).

- **For Learning/Experimentation:** Use the **latest version** (currently JDK 24/25) to see the newest features the language has to offer.

> **Wit & Wisdom:** Using a non-LTS version in a massive production server is like building a skyscraper on a foundation of quicksand. It looks great for six months, but eventually, you're going to have a very sinking feeling when the security updates stop.