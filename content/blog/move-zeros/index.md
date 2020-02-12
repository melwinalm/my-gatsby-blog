---
title: Move Zeros
date: "2020-01-30"
type: problem-solving
description: Move Zeros
tags: csharp
---

Note: This problem was taken from LeetCode - [Move Zeros](https://leetcode.com/problems/move-zeroes/)

Loop through all the elements of the array, if any element is non zero then swap it with the second pointer.

```csharp
public void MoveZeroes(int[] nums) {
    int pointer = 0;
    
    for(int i = 0; i< nums.Length; i++){
        if(nums[i] != 0){
            int temp = nums[pointer];
            nums[pointer] = nums[i];
            nums[i] = temp;
            pointer++;
        }
    }
}
```

This solution has a time complexity of O(n) and space complexity of O(1).
