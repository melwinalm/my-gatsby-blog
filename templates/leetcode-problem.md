---
title: Remove Duplicates from Sorted Array
date: "2020-03-09"
type: problem-solving
description: Remove Duplicates from Sorted Array
tags: csharp
---

Note: This problem was taken from LeetCode - [Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)

### Using HashSet

This problem can be solved using Set. Simply loop through the array and add the values to the HashSet. Now loop through the `Set` and update those values back to the input array. The return value will be the size of the HashSet.

This solution has a time complexity of O(n) and space complexity of O(n).

### Two Pointer Approach

Use two pointers, slow and fast to find the duplicates. The fast pointer checks if its value is the same as the slow pointer. If the values of slow and fast pointers match then increment only the fast pointer. If they differ, then increment the slow pointer and update its value with the value of the fast pointer. Keep doing this until the fast pointer reaches the end of the array.

```csharp
    public int RemoveDuplicates(int[] nums) {
        // If the array length is 0 or 1 then return their length
        if(nums.Length < 2){
            return nums.Length;
        }
        
        int slowPointer = 0;
        int fastPointer = 1;
        
        while(fastPointer < nums.Length){
            if(nums[fastPointer] == nums[slowPointer]){
                fastPointer++;
            }
            else{
                slowPointer++;
                nums[slowPointer] = nums[fastPointer];
                fastPointer++;
                
            }
        }
        return slowPointer+1;
    }
```

This solution has a time complexity of O(n) and space complexity of O(1).

| Approach | Time Complexity | Space Complexity |
| ------------- |:-------------:| :-----:|
| Using HashSet | O(n) | O(n) |
| Two Pointer Approach | O(n) | O(1) |

### Similar Problems
