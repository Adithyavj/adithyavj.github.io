---
title: Data Structures and Algorithms in C#
author: Adithya Vijay
date: 2022-06-01 20:00:00 +0550
categories: [Blogging, Programming]
tags: [development programming dsa c# dotnet6]     # TAG names should always be lowercase
---

### Introduction


### Abstract Data Type
An abstract data type is a class. Data structures are classes that are storing data and acting on it.
Classes contain representation of data and operation on data.

### Big-O Notation
This determines how efficient a piece of code is. It is a way to describe the speed or complexity of a given algorithm.
- O(1) - "Constant" time complexity. It means the code is the most efficient.
Some examples of constant are:
    - Assignments ``` var test = 0; ```
    - Declaration ``` var test; ```
    - Arithmetic ``` 2 + 2 ```
    - Comparison ``` 2 > 1 ```
    - Accessing Element ``` array[1]; ```
    - Calling Function ``` someFunction(); ```
- O(n) - "Linear" time complexity. Here as the values of n increases, the time taken to execute the program goes up in a linear fashion.
Some examples of Linear are:
    - Some type of iteration like for loop, while loop etc

```
int total = 0; O(1)
int i = 2; O(1)

while (i <= 10) O(n)
{
    total = total + i;
    i++;
}

```

> If we have a program with code having O(1) and O(n) complexities, we take the higher no. Thus it being O(n)

- O(n^2) - "Quadratic" time complexity. If the algorithm is O(n^2), then it will have horrible performance. It is also called brute force.
A quadratic algorithm is a : 
    - Nested for loops

```
var n = int.Parse(Console.ReadLine());
for (var r = 1; r <= n; r++)
{
    for (var c = 1; c <= n; c++)
    {
        Console.Write("*");
    }
    Console.WriteLine();
}
```

- log(n)
- n log(n)

![Big-O complexity chart](https://miro.medium.com/max/1200/1*5ZLci3SuR0zM_QlZOADv8Q.jpeg "big-o complexity chart")


### Arrays
Arrays store elements in contiguous (next or together in sequence) memory locations.
Arrays can contain anything of same type with a fixed size.
Arrays are very fast at GET and SET (data retrieval and setting)
Lists<> in C# are actually arrays. 

The main things regarding arrays are inserting values into it (push) and deleting values from it (pop).

1. Insertion
    1.1 Inserting value at the start of an array
        ```
            int[] intArray = new int[6];

            //Make a variable to keep the length because length is based off capacity and doesn't
            // track the actual index.
            int length = 0;
            //Set values to array till index 2
            for (int i = 0; i < 3; i++)
            {
                intArray[length] = i + 1;
                length++;
            }
            //for (int i = 3; i >= 0; i--)
            {
                // this is moving over all the values
                intArray[i + 1] = intArray[i];
            }

            intArray[0] = 20;
        ```
    1.2 Inserting value at the end of an array
        ```
            int[] intArray = new int[6];

            //Make a variable to keep the length because length is based off capacity and doesn't
            // track the actual index.
            int length = 0;

            //Set values to array till index 2
            for (int i = 0; i < 3; i++)
            {
                intArray[length] = i + 1;
                length++;
            }
            // Add value to end of the array
            intArray[length] = 8;
            length++;
        ```
    1.3 Inserting value anywhere in an array
        ```
             int[] intArray = new int[6];

            //Make a variable to keep the length because length is based off capacity and doesn't
            // track the actual index.
            int length = 0;

            //Set values to array till index 2
            for (int i = 0; i < 3; i++)
            {
                intArray[length] = i + 1;
                length++;
            }
            for (int i = 3; i >= 2; i--)
            {
                // Shifting each element one position to the right
                intArray[i + 1] = intArray[i];
            }

            intArray[2] = 34;
        ```

2. Deletion
    2.1 Deleting value from the end of an array
        ```
            int[] intArray = new int[9];

            int length = 0;

            for (int i = 0; i < 6; i++)
            {
                intArray[length] = i + 1;
                length++;
            }
            length--;

            for (int i = 0; i < length; i++)
            {
                Console.WriteLine(intArray[i]);
            }
        ```
    2.2 Deleting value from the start of an array
        ```
            int[] intArray = new int[9];

            int length = 0;

            for (int i = 0; i < 6; i++)
            {
                intArray[length] = i + 1;
                length++;
            }

            for (int i = 1; i < length; i++)
            {
                intArray[i - 1] = intArray[i];
            }

            length--;

            for (int i = 0; i < length; i++)
            {
                Console.WriteLine(intArray[i]);
            }
        ```
    2.3 Deleting value from anywhere in an array
        ```
            // Delete value at 4th position

            for (int i = 0; i < 6; i++)
            {
                intArray[length] = i + 1;
                length++;
            }

            for (int i = 4; i < length; i++)
            {
                intArray[i - 1] = intArray[i];
            }
            length--;

            for (int i = 0; i < length; i++)
            {
                Console.WriteLine(intArray[i]);
            }
        ```

### Linear Search Array
In linear search we use a for loop to loop through the array and a conditional to return true once
the element is found. It traverses the element in an orderly fashion from 0th index to the last index.

```
// key refers to the value we are searching for
bool LinearSearch(int[] array, int key)
{
    for (int i = 0; i <= array.Length; i++)
    {
        if (array[i] == key)
            return true;
    }
    return false;
}
```

### Linked List in C#
It is the ancestor of Lists<> in c#.
Arrays are fixed. We cannot insert values into the middle of an array without it being very expensive to do so.
We can insert anywhere into a linked list and it's dynamic.
Insertions into Linked list have a time complexity of O(1). Best performance

### Stacks in C#
Stack follows Last In First Out method. The last element inserted will be on top of the stack and will be the first one
to go out.
Push - Add a new element
Pop - Remove an element
Peek - Fetch the element present at the top of the Stack

Insertion into stack has a time complexity of O(1)

### Queues in C#
Queues follows First In First Out method.
Enqueue
Dequeue
