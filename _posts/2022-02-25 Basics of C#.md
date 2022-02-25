---
title: Basics of C# Programming Language
author: Adithya Vijay
date: 2022-02-26 00:05:00 +0550
categories: [Blogging, programming]
tags: [development programming csharp]     # TAG names should always be lowercase
---

### Introduction
C# is an object-oriented programming language developed by Microsoft. It enables developers to build applications that run in .NET.
*This brings the question, what is .NET?*
.NET is the managed environment within which C# runs, so you get access to the entire .NET ecosystem, including all packages on nuget.org.

**Code snippet for Hello World program using C#**
```
using System;

class Hello
{
    static void Main()
    {
        Console.WriteLine("Hello, World");
    }
}
```

### Some of the features of the language
- Statically-typed: Identifiers have type set at compile time (not during run time). This gurantees type safety.
- Object-oriented: It is a class based language with features such as inheritance, polymorphism, interfaces, and encapsulation.
- Declarative: Programming what is to be done, as opposed to how it is done.
- Functional: Functions are first-class data types that can be passed as arguments to and returned from other functions.
- Generic: Algorithms are written in terms of types to be specified later when they are instantiated. Here the type will be provided as parameters.
- Lazy (Deferred execution): The compiler will put off evaluating an item until required.
- Integrated Querying: C# has a feature called LINQ (Language Integrated Query), this enable lazy query loading within the language, not only its own objects but, also, external data sources through formats such as XML, JSON, SQL, NoSQL DBs and event streams.
- Type inference: The compiler will often figure out the type of an identifier by itself.

### Platform Support
Initially .NET used to be Windows-only. But with the release of [.NET Core](https://www.microsoft.com/net/core) as well as [Mono](http://www.mono-project.com/), C# can be used in Mac, Linux, and on mobile platforms too.