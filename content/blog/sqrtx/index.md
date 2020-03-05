---
title: Sqrt(x)
date: "2020-03-05"
type: problem-solving
description: Sqrt(x)
tags: csharp
---

Note: This problem was taken from LeetCode - [Sqrt(x)](https://leetcode.com/problems/sqrtx/)

### Naive Approach

The naive way to solve this would be to square the number starting from 0 and see if it is equal to or greater than the given number. This will give you the result.

```csharp
public int MySqrt(int x) {
    if (x <= 1){
        return x;
    } 
    
    int i = 1;
    while(x >= i * i){
        i++;
    }
        
    return i - 1;
}
```

This approach has a time complexity of O(sqrt(n)). See the next approach which solves it logarithmic time complexity.

### Binary Search Approach

Iteratively perform binary search operation to get the required result.

```csharp
public int MySqrt(int x) {
    if(x == 0){
        return 0;
    }
    
    int left = 1;
    int right = x;
    int mid = 0;
    
    while(left <= right){
        mid = left + (right - left)/2;
        if(mid == x / mid){
            return mid;
        }
        else if (mid > x / mid){
            right = mid - 1;
        }
        else{
            left = mid + 1;
        }
    }
    return right;
}
```

### Newtons Method

Initially set `n` the same as the given input number. Then recursively call the Newtons formula to until the difference between `output` and `n` are small. This should give you the required result.

```csharp
public int MySqrt(int x) {
    if(x == 0){
        return 0;
    }
    
    double n = x;
    double output;
    
    while(true){
        output = 0.5 * (n + (x / n));
        if(Math.Abs(output - n) < 0.1){
            break;
        }
        
        n = output;
    }
    
    return (int)output;
}
```
