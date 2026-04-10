---
title: "Day 9 — Understanding Pointers and Struct Mutation in Go"
slug: learning-go-day-9
author: David
pubDate: 2026-04-09 23:03
modDate: 2026-04-09 23:03
categories: ["Tech", "Go"]
---

## Overview

Today I learned one of the most important concepts in Go: **pointers**.

Pointers are essential for understanding how data is passed and modified in Go. This lesson focused on how Go handles values vs references, and how to properly mutate struct data.

---

## What I Built

An enhanced **Student Manager CLI** that:

- uses struct methods with pointer receivers  
- demonstrates value vs pointer behavior  
- updates student data through functions  
- applies bulk updates using a slice of pointers  

---

## Key Concepts

### Pointer Basics

```go
x := 10
p := &x
```

- `&x` gives the memory address  
- `*p` accesses the value  

---

### Pass by Value vs Pointer

```go
func changeScoreValue(s Student)
func changeScorePointer(s *Student)
```

- Value → operates on a copy  
- Pointer → modifies original data  

---

### Pointer Receiver Methods

```go
func (s *Student) addScore(points int)
```

Allows direct modification of struct fields.

---

### Slice of Pointers

```go
[]*Student
```

Used for:

- efficient updates  
- shared data references  

---

### Converting Slice to Pointer Slice

```go
for i := range students {
    ptrs = append(ptrs, &students[i])
}
```

Important to avoid:

```go
for _, s := range students {
    &s // incorrect
}
```

---

## Key Demonstration

```
Before: 80
After value function: 80
After pointer function: 90
```

This clearly shows how pointers allow mutation.

---

## Key Takeaways

- Go is pass-by-value by default  
- Pointers allow modifying original data  
- Pointer receivers are essential for struct methods  
- Use `[]*Type` when you need shared, mutable objects  
- Avoid common mistakes with `range` and pointers  

---

## Reflection

Today’s lesson clarified how Go handles memory and data mutation.

Understanding pointers is critical for writing correct and efficient programs. This concept connects directly to real-world backend development.

---

## Next Steps

- Learn interfaces in Go  
- Understand abstraction and polymorphism  
- Build more modular and reusable code  
