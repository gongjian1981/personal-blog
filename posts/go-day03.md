---
title: Day 3: control flow with if, switch, and for loop
slug: learning-go-day-03
author: David
pubDate: 2026-04-03 23:35
modDate: 2026-04-03 23:35
categories: ["Tech", "Go"]
---

Today's knowelege is quite simple:

# Key Concepts

## if

- Basic form
  
  ```
  for condition {
    // body
  } else {
    // body
  }
  ```
- Parentheses are unnecessary and not idiomatic
  
  ```
  for n > 0 {
    fmt.Println("Positive")
  }
  ```

### switch

- Basic form
  
  ```
  day := 3
  
  switch day {
  case 1:
    fmt.Println("Monday")
  case 2:
    fmt.Println("Tuesday")
  default:
    fmt.Println("Unknown")
  }
  ```

- No break needed

- Multiple conditions
  
  ```
  score := 85
  
  switch {
  case score >= 90:
      fmt.Println("A")
  case score >= 80:
      fmt.Println("B")
  case score >= 70:
      fmt.Println("C")
  default:
      fmt.Println("D")
  }
  ```

### for

- there's no `while` in *go*

- 
  ```
  for i := 0; i < 5; i++ {
    fmt.Println(i)
  }
  ```