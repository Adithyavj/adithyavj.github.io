---
title: C# Basic Concepts
author: Adithya Vijay
date: 2022-02-26 00:30:00 +0550
categories: [Blogging, programming]
tags: [development programming csharp]     # TAG names should always be lowercase
---

### Introduction
C# is a statically-typed programming language, meaning everything will have a type at compile-time. When we assing a value to a name, it is called as defining a variable.
We can define a variable either by explicitly specifying it's type or by letting the complier infer it's type based on the assigned value(*type inference*).
```
int expVar = 7; // Explicitly typed
var impVar = 7; // Implicitly typed
```

### Object Oriented Concepts
- C# is an object-oriented language and requires all the functions to be defined in a class.
- The class keyword is used to define a class.
- Objects (or instances) are created by using the new keyword.

```
// Declaring a class
class Calculator
{
    // ...
}

// Creating an instance of the class
var calculator = new Calculator();
```

- A function within a class is referred to as a *method*. 
- Each method can have zero or more parameters. 
- All parameters must be explicitly typed, there is no type inference for parameters
- The return type must also be made explicit.
- Values are returned from methods using the return keyword. To allow a method to be called by code in other files, the public access modifier must be added.

```
class Calculator
{
    public int Add(int x, int y)
    {
        return x + y;
    }
}
```

- Methods are invoked using dot (.) syntax on an instance

```
var calculator = new Calculator();
var sum_v1 = calculator.Add(1, 2);
var sum_v2 = calculator.Add(x: 1, y: 2);
```

- Scope in C# is defined between the { and } characters.
- C# supports single line comments ```//``` and multi-line comments inserted betewwn ```/*``` and ```*/```