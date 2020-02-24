---
title: Missing Number
date: "2020-02-18"
type: problem-solving
description: Missing Number
tags: csharp
---

Note: This problem was taken from LeetCode - [Missing Number](https://leetcode.com/problems/missing-number/)

### Best Approach

Actual Sum of n numbers is given by n(n+1)/2. That will be your actual sum. Find the sum of all the numbers in the given array, that will be your given sum. The difference between the actual sum and the given sum will give you the missing number.

```csharp
public int MissingNumber(int[] nums) {
    int N = nums.Length;
    int givenSum = 0;
    int actualSum = (N * (N + 1))/2;
    
    foreach(int num in nums){
        givenSum += num;
    }
    
    return actualSum - givenSum;
}
```

The above solution has a time complexity of O(n) with a constant space requirement.
