---
title: Merge Sorted Array
date: "2020-03-12"
type: problem-solving
description: Merge Sorted Array
tags: csharp
---

Note: This problem was taken from LeetCode - [Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/submissions/)

### Naive Approach

Start two pointers from the end of both the lists and push the value which is higher than the other. Keep doing this until one of the pointers reaches 0.

```csharp
public void Merge(int[] nums1, int m, int[] nums2, int n) {
    int mPointer = nums1.Length - 1;
    int fPointer = m - 1;
    int sPointer = n - 1;
    
    while(fPointer >= 0 && sPointer >= 0){
        if(nums2[sPointer] >= nums1[fPointer]){
            nums1[mPointer] = nums2[sPointer];
            sPointer--;
        }
        else{
            nums1[mPointer] = nums1[fPointer];
            fPointer--;
        }
        
        mPointer--;
    }

    // This is required in certain edge cases when fPointer has reached 0th index and sPointer has still some elements that are to be moved to the num1 array
    while(sPointer >= 0){
        nums1[mPointer] = nums2[sPointer];
        sPointer--;
        mPointer--;
    }
}
```
