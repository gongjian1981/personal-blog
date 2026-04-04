---
title: Day 2 of Learning Go: Variables, Types, and CLI Input
slug: learning-go-day-02
author: David
pubDate: 2026-04-02 23:55
modDate: 2026-04-02 23:55
categories: ["Tech", "Go"]
---

Today's knowelege is quite simple:

# Key Concepts

## variable

1. Use `var` to declare a variable

2. use 
   
   ```
   var a int = 30
   ```
   
   to declear a as a integer type, or just use `:=` like:
   
   ```
   a := 100
   ```
   
   to let Go infer the type automatically

### 

### Data Type

basic data types:

- int

- float64

- string

- bool



### Cli Input

use `fmt.Scan()` to get user input

the parameter should be a pointer, so use `&` in front of the varibale



### Print Formatting

use `fmt.Printf()` to format output, common format verbs:

- %s -> string

- %d -> integer

- %f -> float

- %v -> any type(generic)




