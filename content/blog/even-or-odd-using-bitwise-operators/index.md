---
title: Even or Odd using Bitwise Operators
date: "2020-03-16"
type: problem-solving
description: Even or Odd using Bitwise Operators
tags: csharp
---

### Problem Statement

Find if a given number is odd or even using bitwise operators

### Solution

Simply perform an `XOR` operation between the given number and `1` to get the desired result. The last bit of an odd number will be one and `XOR`ing it with 1 will reduce the number by 1. And `XOR`ing an even number with 1 will increase the number by 1. Use this technique to get the required result

```csharp
public static bool IsEven(int num)
{
    if ((num ^ 1) == (num + 1))
    {
        return true;
    }
    else
    {
        return false;
    }
}
```
