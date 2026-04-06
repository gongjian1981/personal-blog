---
title: "Day 5 of Learning Go: Understanding Slices and a Tricky Bug"
slug: learning-go-day-05
author: David
pubDate: 2026-04-05 23:18
modDate: 2026-04-05 23:18
categories: ["Tech", "Go"]
---

# Overview

Today I focused on Go’s core collection type: slices. Instead of treating this as a syntax exercise, I built a small CLI tool to process a list of integers and used it to explore common patterns and pitfalls.

The goal was to move from “knowing slices” to using them correctly under real conditions.

---

# What I Built

A simple Number List Analyzer that:

- reads a dynamic list of integers from user input
- computes aggregate metrics (sum, max, even count)
- filters values based on a condition
- reverses the sequence

This forced me to work with:
- dynamic allocation (make)
- iteration patterns (range, index-based loops)
- slice transformations

---

# Key Implementation Patterns

Slice initialization

nums := make([]int, n)

Using make ensures the slice has the correct length for indexed assignment during input.

---

Iteration (idiomatic Go)
```
for _, num := range nums {
    total += num
}
```
Using range improves readability and avoids unnecessary indexing when the index is not needed.

---

Building derived slices
```
result := []int{}
for _, num := range nums {
    if num > 10 {
        result = append(result, num)
    }
}
```
This pattern is fundamental for filtering and transformation.

---

Subtle Bug: Slice Aliasing

Initial implementation
```
newArray := nums[0:0]
```
At first glance, this looks like an efficient way to reuse memory. However, this introduces aliasing: both slices share the same underlying array.

Consequence

Appending to newArray modified the original nums, leading to incorrect downstream results (e.g., reverse output).

This is a classic example of Go’s slice semantics causing unexpected side effects.

---

Fix
```
newArray := []int{}
```
By allocating a new slice, I ensured isolation between data structures.

---

Key Takeaways

- A slice is a descriptor over an underlying array, not a standalone container
- Slicing (nums[0:0]) can introduce shared memory bugs
- append may mutate existing memory if capacity allows
- Clear ownership of data matters—even in small programs

This is a good reminder that Go trades abstraction for performance transparency. You get control, but you are also responsible for understanding the memory model.

---

Reflection

This was the first time I ran into a bug that wasn’t about syntax or logic, but about data structure behavior.

Understanding why the bug happened—not just fixing it—was the most valuable part of today’s work.

---

Next Steps

- Work with maps for key-value data
- Implement frequency counting patterns
- Start solving more problem-oriented tasks instead of linear scripts
