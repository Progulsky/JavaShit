---
tags:
  - "#java"
  - "#java_core"
  - class
  - text
---
# String

**Related notes:** [[Class]], [[Text_Block]], [[Formatting]]

---

A **String** is a built-in class that represents a sequence of characters. While it feels like a primitive type because of how often we use it, it is actually a **Reference Type** (an Object). Strings are essentially arrays of Unicode characters wrapped in a powerful API. It uses double quotes `"` to store literals. String literals can be letters, numbers, symbols or any Unicode characters

---

### The Golden Rule: Immutability

The most critical feature of a String is that it is **immutable**. Once a String object is created in memory, its value **cannot be changed**.

- When you perform an operation like `concat()` or `toUpperCase()`, Java does not modify the original string.
    
- Instead, it creates a **completely new String object** with the result.
    
- The original string remains unchanged in memory until the Garbage Collector removes it.

---

### String Methods

#### 1. Inspection Methods

These methods allow you to "look into" the string without changing anything.

- **`length()`**: Returns the count of characters.
    
- **`charAt(index)`**: Gets the character at a specific position (starts at 0).
    
- **`indexOf()` / `lastIndexOf()`**: Finds the position of a character or substring. Both methods can take two parameters: what to search for and starting position (optional) — where the search begins in the string
    
- **`isEmpty()` vs. `isBlank()`**: `isEmpty()` checks if length is 0; `isBlank()` returns true even if the string contains only spaces/tabs.

#### 2. Comparison Methods

In Java, **never use `==` to compare string values**; always use these methods:

- **`regionMatches()`**: Returns boolean, if defined sub-regions are matched.
    
- **`equals()`**: Checks if the content is identical.
    
- **`equalsIgnoreCase()`**: Checks content while ignoring capital/lowercase differences.
    
- **`contains()`**: Checks if a specific sequence exists anywhere inside the string.
    
- **`contentEquals`**: Returns boolean if the String's value is equal to the value of the argument passed. This method allows for arguments other than String, for any type that is a character sequence
    
- **`startsWith()` / `endsWith()`**: Checks the boundaries of the string.

#### 3. Manipulation Methods

Since strings are immutable, these methods all return a **new** string.

- **`indent`**: Adds or removes spaces from the beginning of lines in multi-line text
    
- **`toLowerCase, toUpperCase`**: Returns a new String, either in a lower case or in upper case
    
- **`strip()` vs. `trim()`**: `trim()` is the older version (removes basic spaces); `strip()` (Java 11+) is smarter and removes all Unicode-defined whitespace.
    
- `concat`: Works like the plus operator for strings. Joins (concatenates) one string to another; you can stack them. Returns a new string.
    
- `join`: Allows multiple strings to be concatenated together in a single method, specifying a delimiter
    
- `repeat`: Returns String repeated by thee number of times specified in the argument
    
- `replace, replaceAll, replaceFirst`: These methods replace characters or substrings in the strings, returning a new string with replacements made
    
- `substring, subSuquence`: These return a part of the String, its range defined by the start and end index specified

---

### StringBuilder: The Mutable Alternative

If you are in a situation where you need to modify a string thousands of times (like inside a loop), using `String` is slow because it creates thousands of temporary objects. **StringBuilder** solves this by providing a **mutable** sequence of characters.

#### The ways to create StringBuilder object

- Pass a String - `new StringBuilder("Hello")`'
    
- Pass no arguments at all - `new StringBuilder()`
    
- Pass integer value - `new StringBuilder(5)`
    
- Pass some other type of character sequence - `new StringBuilder(StringBuilder)`

#### Key Features

- **Efficiency:** Modifies the internal character array directly without creating new objects.
    
- **Append & Insert:** Easily add data to the end or middle of the sequence.
    
- **Capacity:** StringBuilder reserves extra space (default is 16 characters + the initial length) so it doesn't have to resize the internal array constantly.

```
StringBuilder sb = new StringBuilder("Hello");
sb.append(" World")     // "Hello World"
  .insert(5, ",")       // "Hello, World"
  .reverse();           // "dlroW ,olleH"

String finalResult = sb.toString(); 
```

#### Common Methods

- `append` - adds text to the end
    
- `insert` - inserts text at a specific index
     
- `delete, deleteCharAt` - deletes characters in a range or index 
    
- `replace` - replaces characters in a range
    
- `reverse` - reverses the character sequence
    
- `toString` - converts the builder into a String
    
- `setLenth` - used to truncate the sequence or include null sequences to fill out the sequence to that length
    
- `capacity` -  returns current capacity
    
- `trimToSize` - reduces capacity to match the current length

---

### Capacity vs. Length

- **Length:** The number of characters currently in the builder.
    
- **Capacity:** The total amount of characters the builder _can_ hold before the JVM is forced to resize the internal memory.

> **Witty Note:** Using `String` for heavy concatenation is like buying a new car every time you need to change your lane. Using `StringBuilder` is like actually using the steering wheel.