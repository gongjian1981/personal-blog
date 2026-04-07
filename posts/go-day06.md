---
title: "Day 6 — Using Maps for Frequency Analysis in Go"
slug: learning-go-day-6
author: David
pubDate: 2026-04-06 23:38
modDate: 2026-04-06 23:38
categories: ["Tech", "Go"]
---

## Overview

Today I focused on Go’s `map` type and applied it to a classic problem: **frequency counting**.

Instead of just learning syntax, I implemented a small CLI tool that processes a list of integers and extracts useful insights from it.

This is a key step toward writing **interview-ready code**, since maps and frequency patterns appear frequently in real-world problems.

---

## What I Built

A **Frequency Analyzer CLI** that:

- reads a list of integers from user input  
- builds a frequency map (`map[int]int`)  
- identifies the most frequent number  
- counts distinct values  
- finds numbers that appear exactly once  

---

## Key Concepts

### 1. Maps in Go

```go
m := make(map[int]int)
```

Maps store key-value pairs and are used for fast lookups and counting.

---

### 2. Frequency Counting Pattern

```go
for _, num := range nums {
    freq[num]++
}
```

This is one of the most important patterns in programming and is widely used in interviews.

---

### 3. Iteration over Maps

```go
for k, v := range freq {
    fmt.Println(k, v)
}
```

- Order is not guaranteed  
- Map iteration is inherently unordered  

---

## Functions Implemented

### Build Frequency Map
```go
func buildFrequency(nums []int) map[int]int
```

### Find Most Frequent Element
```go
func mostFrequent(freq map[int]int) (int, int)
```

### Count Distinct Values
```go
func countUnique(freq map[int]int) int
```

### Find Single-Occurrence Values
```go
func findSingles(freq map[int]int) []int
```

---

## Key Issue Encountered

### Map Iteration Order

I initially assumed that map iteration had a consistent order, but Go maps are **unordered**.

This means:

- The “last” element is not meaningful  
- Results may vary between runs  

### Resolution

I updated the logic to either:
- accept arbitrary results, or  
- define a deterministic rule (e.g., choose the smallest value in case of ties)

---

## Key Takeaways

- Maps are essential for counting and grouping data  
- `freq[num]++` is the idiomatic way to count  
- Map iteration order is not guaranteed  
- Always define clear behavior for edge cases (e.g., ties, empty input)  
- Distinguish between:
  - **distinct values** (`len(map)`)
  - **single-occurrence values** (`count == 1`)

---

## Example Output

```
How many numbers? 6
Next number: 1
Next number: 2
Next number: 2
Next number: 3
Next number: 3
Next number: 3

Numbers: [1 2 2 3 3 3]

Frequency:
1 -> 1
2 -> 2
3 -> 3

Most frequent: 3 (count: 3)
Unique count: 3
Singles: [1]
```

---

## Reflection

This exercise reinforced how powerful maps are for solving real problems.

It also highlighted an important concept: **understanding behavior (like map ordering) is just as important as writing correct syntax**.

---

## Next Steps

- Work with strings and maps together  
- Solve problems like:
  - character frequency  
  - anagram detection  
- Continue building interview-style problem-solving skills
