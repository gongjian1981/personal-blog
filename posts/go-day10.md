---
title: "Day 10 — Interfaces and Polymorphism in Go"
slug: learning-go-day-10
author: David
pubDate: 2026-04-10 19:15
modDate: 2026-04-10 19:15
categories: ["Tech", "Go"]
---

## Overview

Today I learned how to use **interfaces** in Go to design flexible and reusable code.

Interfaces allow different types to share common behavior without explicit inheritance. This enables polymorphism and decouples implementation from usage.

---

## What I Built

A **Grading System CLI** that:

- defines a common interface (`Evaluator`)
- implements it for multiple types (`Student`, `Course`)
- stores different types in a single slice (`[]Evaluator`)
- evaluates and prints results in a unified way

---

## Key Concepts

### Interface Definition

type Evaluator interface {
    Evaluate() string
}

An interface defines behavior, not data.

---

### Implicit Implementation

func (s Student) Evaluate() string  
func (c Course) Evaluate() string  

Any type that implements the required method automatically satisfies the interface.

---

### Polymorphism with Interface Slice

evaluators := []Evaluator{}

Allows storing different types (Student, Course) together.

---

### Stringer Interface

func (s Student) String() string

Improves output readability when printing.

---

## Example Output

Student Alice -> B  
Student Bob -> F  
Course Math -> A  

---

## Key Takeaways

- Interfaces define behavior, not structure  
- Go uses implicit interface implementation  
- Interfaces enable polymorphism  
- []Interface allows mixing different types  
- Clean design comes from separating behavior from data  

---

## Reflection

This was the first step into designing systems instead of just writing functions.

Interfaces make code more flexible and closer to real-world backend development.

---

## Next Steps

- Learn error handling  
- Work with files and real data  
- Structure code into packages  
