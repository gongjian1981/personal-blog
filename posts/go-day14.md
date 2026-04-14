---
title: "Day 14 — Student Report Generator (Final Project)"
slug: learning-go-day-14
author: David
pubDate: 2026-04-14 00:11
modDate: 2026-04-14 00:11
categories: ["Tech", "Go"]
---

## Overview

This project is a **modular, data-driven Go application** that reads student data from a file, processes it, and generates a structured report.

It demonstrates core backend engineering concepts:

- file I/O
- error handling
- modular design (packages)
- data processing
- clean output formatting

---

## Features

- Read student data from `input.txt`
- Parse structured records into Go structs
- Skip invalid input lines safely
- Compute:
  - Average score
  - Top-performing students (supports ties)
  - Grade distribution
- Generate a formatted report
- Write results to `output.txt`

---

## Project Structure

```
day14-student-report/
├── go.mod
├── main.go
├── input.txt
├── output.txt
└── student/
    ├── model.go
    ├── reader.go
    ├── processor.go
    └── writer.go
```

---

## Architecture

### 1. `main.go`
- Entry point
- Orchestrates workflow:
  - read → process → write
- Handles high-level errors

---

### 2. `student/model.go`
Defines core data structure:

```go
type Student struct {
    Name  string
    Age   int
    Score int
}
```

---

### 3. `student/reader.go`
- Reads file using `bufio.Scanner`
- Parses each line
- Skips invalid data safely

---

### 4. `student/processor.go`
Business logic:

- `AverageScore`
- `TopStudents`
- `GradeDistribution`

---

### 5. `student/writer.go`
- Writes final report using `os.WriteFile`

---

## Input Format (`input.txt`)

```
Alice 20 85
Bob 22 70
Charlie 19 95
David 21 95
```

Invalid lines are ignored safely.

---

## Output Example (`output.txt`)

```
--- Student Report ---

Average Score: 78.10

Top Students:
- Charlie (95)
- David (95)

Grade Distribution:
A: 3
B: 2
C: 2
D: 2
F: 1
```

---

## How to Run

From project root:

```
go run .
```

---

## Error Handling Strategy

- File errors → returned and handled in `main`
- Parsing errors → logged and skipped
- Scanner errors → checked explicitly
- No `panic` used in normal flow

---

## Key Learnings

- Structuring Go projects using packages
- Separating concerns across modules
- Building data-processing pipelines
- Writing robust, fault-tolerant code
- Producing clean, formatted output

---

## Reflection

This project represents the transition from:

```
learning syntax → building real applications
```

It combines all prior concepts into a cohesive system and resembles a simplified backend data-processing service.

---

## Next Steps

- Add CLI arguments (input/output paths)
- Support CSV or JSON formats
- Add logging (e.g., `log` package)
- Expose functionality via HTTP API

---

## Summary

Day 14 marks the completion of a foundational Go learning path.

The result is a **portfolio-ready project** demonstrating:

- clean code structure
- practical problem-solving
- readiness for backend development work
