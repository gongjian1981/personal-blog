---
title: "Day 12 — Building Data-Driven Programs with File I/O in Go"
slug: learning-go-day-12
author: David
pubDate: 2026-04-12 17:18
modDate: 2026-04-12 17:18
categories: ["Tech", "Go"]
---

## Overview

Today I transitioned from interactive CLI programs to data-driven applications.

Instead of relying on terminal input, the program reads structured data from a file, processes it, and writes results back to disk. This is a foundational pattern for backend services and data processing tools.

---

## What I Built

A Student Data Processor that:

- reads student records from a file (students.txt)
- parses each line into a Student struct
- computes aggregate metrics (average score)
- finds top-performing students (supports ties)
- writes results to an output file (result.txt)
- handles errors at every step

---

## Input Format

students.txt:

Alice 20 85
Bob 22 70
Charlie 19 95

Each line:

Name Age Score

---

## Core Data Model

type Student struct {
    Name  string
    Age   int
    Score int
}

---

## Key Implementation Patterns

### Open file safely

file, err := os.Open("students.txt")
if err != nil {
    return nil, err
}
defer file.Close()

---

### Read line-by-line

scanner := bufio.NewScanner(file)

for scanner.Scan() {
    line := scanner.Text()
}

---

### Check scanner errors

if err := scanner.Err(); err != nil {
    return nil, err
}

---

### Parse structured data

var s Student
_, err := fmt.Sscanf(line, "%s %d %d", &s.Name, &s.Age, &s.Score)

---

### Skip invalid lines

student, err := stringToStudent(line)
if err != nil {
    fmt.Println("Skipping invalid line:", line)
    continue
}

---

### Write results

output := fmt.Sprintf("Average Score: %.2f
", avg)
os.WriteFile("result.txt", []byte(output), 0644)

---

## Example Output

Average Score: 83.33
Top Student: Charlie (95)

---

## Key Takeaways

- File I/O enables real-world data processing
- bufio.Scanner is standard for reading files
- Always defer file.Close()
- Always check scanner.Err()
- Convert raw input into structs
- Prefer robustness over crashing

---

## Reflection

This exercise introduced a common backend pattern:

Input → Parse → Process → Output

This is widely used in backend systems and data pipelines.

---

## Next Steps

- Organize code into packages (Day 13)
- Improve validation
- Build a small multi-file project
