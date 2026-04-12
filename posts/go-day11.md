---
title: "Day 11 — Error Handling in Go"
slug: learning-go-day-11
author: David
pubDate: 2026-04-11 19:15
modDate: 2026-04-11 19:15
categories: ["Tech", "Go"]
---

## Overview

Today I learned how Go handles errors explicitly through the `error` type.

Unlike languages that rely on exceptions, Go treats errors as ordinary values. This makes control flow more visible and forces programmers to handle failures directly.

---

## What I Built

A Safe Calculator CLI that:

- reads user input safely
- performs division with validation
- computes square roots with validation
- uses a custom error type
- handles all returned errors explicitly

---

## Key Concepts

### Errors Are Values

In Go, functions often return:

```go
value, err := someFunction()
```

Then the caller checks:

```go
if err != nil {
    // handle error
}
```

This is the standard Go pattern.

---

### Custom Error Type

```go
type MyError struct {
    Message string
}

func (e MyError) Error() string {
    return e.Message
}
```

By implementing `Error() string`, a type satisfies the built-in `error` interface.

---

### Safe Division

```go
func safeDivide(a, b int) (int, error)
```

Returns an error when attempting to divide by zero.

---

### Safe Square Root

```go
func safeSqrt(x float64) (float64, error)
```

Returns an error when attempting to calculate the square root of a negative number.

---

### Input Validation

Used `fmt.Scan` together with error checking to validate user input before performing calculations.

---

## Example Output

```text
Enter two integers: 10 0
Error: cannot divide by zero

Enter a number to find its square root: -4
Error: cannot take square root of a negative number
```

---

## Key Takeaways

- Go uses explicit error handling instead of exceptions
- The `error` interface is central to real-world Go code
- Returning `(value, error)` is a core design pattern
- Custom error types are useful when more control is needed
- Every user input and operation should be validated

---

## Reflection

This lesson made Go feel much closer to production code.

Error handling changes the way programs are written: instead of assuming success, the code must always consider what can go wrong. That mindset is essential for backend engineering.

---

## Next Steps

- Work with files and file errors
- Combine file I/O with error handling
- Start writing programs that process real data instead of only terminal input
