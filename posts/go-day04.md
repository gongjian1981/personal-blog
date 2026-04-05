---
title: "Day 4: functions"
slug: learning-go-day-04
author: David
pubDate: 2026-04-04 23:18
modDate: 2026-04-04 23:18
categories: ["Tech", "Go"]
---

Today's knowelege is functions:

# Key Concepts

- Basic form
  
  ```
  func add(a int, b int) int {
    return a + b
  }
  ```
  
- Usage
  
  ```
  result := add(1, 2)
  ```

- Cleaner syntax (same type)
  
  ```
  func add(a, b int) int {
    return a + b
  }
  ```

- Multiple Return Values
  
  ```
  func divide(a, b int) (int, int) {
    return a / b, a % b
  }
  ```
  Usage
  ```
  q, r := divide(10, 3)
  ```
  Ignoring Values
  ```
  q, _ := divide(10, 3)
  ```
  

- Named Return Values
  ```
  func rectangle(width, height int) (area int) {
    area = width * height
    return
  }
  ```