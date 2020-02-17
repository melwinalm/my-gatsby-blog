---
title: Single Number
date: "2020-02-04"
type: problem-solving
description: Single Number
tags: csharp
---

Note: This problem was taken from LeetCode - [Single Number](https://leetcode.com/problems/single-number/)

### Using Hashtable

This can be solved using a hashtable or a set. But this solution takes linear space. Can we solve using constant space? See the next approach. 

### Using Bitwise XOR

Perform bitwise XOR operation iteratively on all the elements of the array. The repeated elements will be cancelled out during this operation, except for the number which has occurred only twice. See the code below for the solution.

```csharp
public int SingleNumber(int[] nums) {
    int num = 0;
    
    for(int i = 0; i < nums.Length; i++){
        num ^= nums[i];
    }
    
    return num;
}
```

### Time and Space Complexities 

| Approach | Time Complexity | Space Complexity |
| ------------- |:-------------:| :-----:|
| Hashtable or Set | O(n) | O(n) |
| Bitwise XOR | O(n) | O(1) |
