---
title: "Day 8 — Structs and Data Modeling in Go"
slug: learning-go-day-8
author: David
pubDate: 2026-04-08 23:53
modDate: 2026-04-08 23:53
categories: ["Tech", "Go"]
---

## Overview

Today I moved from simple procedural code to structured programming using Go structs.

The focus was on modeling real-world data (students) and organizing logic around that model. This is a key step toward writing code that resembles real backend systems.

---

## What I Built

A Student Manager CLI that:

- collects student data (name, age, score)
- stores data using a struct
- computes average score
- finds the top student
- filters passing students
- sorts students by score (descending)

---

## Key Concepts

### Struct Definition

type Student struct {
    Name  string
    Age   int
    Score int
}

Structs allow grouping related data into a single, type-safe structure.

---

### Slice of Structs

students := make([]Student, 0, n)

This enables managing a collection of structured records.

---

### Struct Methods

func (s Student) isPassing() bool {
    return s.Score >= 60
}

Methods attach behavior to data, making code more modular.

---

### Data Processing Functions

- averageScore
- topStudent
- passingStudents
- custom sort

---

## Key Issues Encountered

### Function vs Method

Wrong:

func isPassing(s Student) bool

Correct:

func (s Student) isPassing() bool

---

### Top Student Initialization

Unsafe:

maxScore := 0

Better:

top := students[0]

---

### Preallocation

make([]Student, 0, n) avoids repeated memory allocation.

---

## Key Takeaways

- Structs model real-world data
- Methods improve structure and readability
- Struct + slice is a core Go pattern
- Always consider edge cases

---

## Reflection

Today marked a shift from writing small scripts to building structured programs.

---

## Next Steps

- Learn pointers
- Understand value vs reference
- Use pointer receivers
