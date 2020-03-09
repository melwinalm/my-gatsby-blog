---
title: Find Nth Fibonacci Number
date: "2020-03-09"
type: problem-solving
description: Find Nth Fibonacci Number
tags: csharp
---

Note: This problem was taken from the Daily Coding Problem #233

### Problem Statement

This problem was asked by Apple.

Implement the function fib(n), which returns the nth number in the Fibonacci sequence, using only O(1) space.

```csharp
public int fib(int N)
{
    if(N < 2)
    {
        return N;
    }
    int prev = 0;
    int curr = 1;

    for(int i = 0; i < N -1; i++)
    {
        int temp = prev + curr;
        prev = curr;
        curr = temp;
    }

    return curr;
}
```
