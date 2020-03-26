---
title: Number of Steps to Reduce a Number to Zero
date: "2020-03-25"
type: problem-solving
description: Number of Steps to Reduce a Number to Zero
tags: csharp
---

Note: This problem was taken from LeetCode - [Number of Steps to Reduce a Number to Zero](https://leetcode.com/problems/number-of-steps-to-reduce-a-number-to-zero/)

```csharp
public int NumberOfSteps (int num) {
    int count = 0;
    
    while(num != 0){
        if(num % 2 == 0){
            num /= 2;
        }
        else{
            num -= 1;
        }
        count++;
    }
    
    return count;
}
```
