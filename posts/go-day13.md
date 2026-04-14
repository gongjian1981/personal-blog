---
title: "Day 13 — Student Manager (Modular Go Project)"
slug: learning-go-day-13
author: David
pubDate: 2026-04-13 20:45
modDate: 2026-04-13 20:45
categories: ["Tech", "Go"]
---

## Overview

This project demonstrates how to structure a Go application using packages and modular design.

Instead of placing all logic in a single file, the program is organized into reusable components, following real-world Go project practices.

---

## Features

- Read student data from a file
- Parse structured data into Go structs
- Compute:
  - Average score
  - Top-performing students (supports ties)
- Skip invalid input lines safely
- Write results to an output file
- Organized using custom packages

---

## Project Structure

day13-student-manager/
├── go.mod
├── main.go
├── students.txt
└── student/
    ├── student.go
    └── processor.go

---

## Design Highlights

### Package Separation

- main.go: entry point, orchestration
- student/: business logic and data model

---

## Input Format

students.txt:

Alice 20 85
Bob 22 70
Charlie 19 95

Each line: Name Age Score

---

## Output

result.txt:

Average Score: 83.33
Top Student: Charlie (95)

---

## How to Run

go run .

---

## Error Handling

Handles:
- file errors
- invalid lines
- scan errors
- write failures

---

## Key Learnings

- Go package structure
- Export rules
- Separation of concerns
- File I/O + structs

---

## Reflection

Transition from single-file scripts to modular applications.

---

## Next Steps

- Add logging
- Support JSON/CSV
- Add CLI flags
- Build API layer
