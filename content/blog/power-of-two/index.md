---
title: Power of Two
date: "2020-03-20"
type: problem-solving
description: Power of Two
tags: csharp
---

Note: This problem was taken from LeetCode - [Power of Two](https://leetcode.com/problems/power-of-two/)

### Iterative Approach

Keep dividing the given number by 2 until reaches 1.

```csharp
public bool IsPowerOfTwo(int n) {
    // return false if the given number is a negative number or zero
    if(n <= 0){
        return false;
    }
    
    while(n % 2 == 0){
        n /= 2;
    }
    
    return n == 1;
}
```

### Bitwise Approach

If the given number is a power of 2 then the binary form of that number will have all of its bits as 0 except for the most significant bit which will be 1. Simply perform an `AND` operation with `n-1` which have all the bits 1 except for the MSB which will be 0. If the `AND` operation returns zero then it's a power of two. 

```csharp
  public bool IsPowerOfTwo(int n) {
      if(n <= 0){
          return false;
      }
      
      return (n & (n - 1)) == 0;
  }
```
