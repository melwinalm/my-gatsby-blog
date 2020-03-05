---
title: Largest Perimeter Triangle
date: "2020-03-05"
type: problem-solving
description: Largest Perimeter Triangle
tags: csharp
---

Note: This problem was taken from LeetCode - [Largest Perimeter Triangle](https://leetcode.com/problems/largest-perimeter-triangle/)

For a triangle to be valid, the value of the longest side of the triangle must be less than the sum of the other two sides of the triangle i.e, `c < a + b`. Use this condition to find the triangle with the highest perimeter.

First, sort the given input, then starting from the end of the array, check if the last three values of the array satisfy the above condition. Keep doing this until you find the numbers which satisfy the condition. 

```csharp
public int LargestPerimeter(int[] A) {
    
    if(A.Length < 3){
        return 0;
    }
    
    Array.Sort(A);
    
    for(int i = A.Length - 1; i >= 2; i-- ){
        if(A[i-1] + A[i-2] > A[i]){
            return A[i] + A[i-1] + A[i-2];
        }
    }
    
    return 0;
}
```
