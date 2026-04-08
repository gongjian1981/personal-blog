---
title: "Day 7 — String Processing and Anagram Detection in Go"
slug: learning-go-day-7
author: David
pubDate: 2026-04-07 22:43
modDate: 2026-04-07 22:43
categories: ["Tech", "Go"]
---

## Overview

Today I worked on combining **strings, runes, and maps** to solve practical problems such as character counting and anagram detection.

This is an important step toward writing **interview-ready code**, since string processing combined with hash maps is one of the most common problem patterns.

---

## What I Built

A **String Analyzer CLI** that:

- reads a string input  
- computes character frequency  
- counts vowels  
- reverses the string  
- checks whether two strings are anagrams  
- supports a normalized anagram check (ignoring case and spaces)  

---

## Key Concepts

### 1. Iterating Over Strings (Runes)

```go
for _, ch := range s {
    // ch is a rune (Unicode character)
}
```

- Go strings are UTF-8 encoded  
- Using `range` ensures correct handling of Unicode characters  

---

### 2. Character Frequency Map

```go
freq := make(map[rune]int)
for _, ch := range s {
    freq[ch]++
}
```

This is a core pattern used in many interview problems.

---

### 3. Unicode-Safe String Reversal

Incorrect approach (byte-based):

```go
len(s)
```

Correct approach:

```go
runes := []rune(s)
```

Then reverse using two pointers:

```go
for i, j := 0, len(runes)-1; i < j; i, j = i+1, j-1 {
    runes[i], runes[j] = runes[j], runes[i]
}
```

---

### 4. Anagram Detection

Basic idea:

- Two strings are anagrams if they have the same character counts  

Efficient solution:

```go
freq := make(map[rune]int)

for _, ch := range a {
    freq[ch]++
}
for _, ch := range b {
    freq[ch]--
}
```

Then check all values are zero.

---

### 5. Normalization for Advanced Anagram

To support:

- case-insensitive comparison  
- ignoring spaces  

Normalize first:

```go
func normalizeString(s string) string
```

Then reuse the same anagram logic.

---

## Key Issues Encountered

### 1. Unicode Bug in String Reversal

Using `len(s)` (bytes) instead of rune length caused incorrect reversal for non-ASCII strings.

### Fix

Convert to `[]rune` before processing.

---

### 2. Input Limitation with fmt.Scan

`fmt.Scan` only reads up to whitespace, which prevents testing phrases like:

```
dirty room
```

This affects advanced anagram testing.

---

### 3. Map Iteration Order

Maps in Go are unordered, so output order may change between runs.

This is expected behavior.

---

## Key Takeaways

- Always use `[]rune` for Unicode-safe string operations  
- `map[rune]int` is essential for string frequency problems  
- Normalize input before comparison when needed  
- Avoid assumptions about map ordering  
- Understand input limitations of `fmt.Scan`  

---

## Example Output

```
Enter a string: hello

Frequency:
h -> 1
e -> 1
l -> 2
o -> 1

Vowel count: 2
Reversed: olleh

Second string: olleh
Anagram: true
```

---

## Reflection

Today’s work was more than just syntax practice. It highlighted how subtle issues—like Unicode handling and input methods—can affect correctness.

Understanding these details is essential for writing robust and production-quality Go code.

---

## Next Steps

- Learn structs to model real-world data  
- Combine structs with slices and maps  
- Start building more realistic programs  
