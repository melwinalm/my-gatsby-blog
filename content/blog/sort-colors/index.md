---
title: Sort Colors
date: "2020-02-25"
type: problem-solving
description: Sort Colors
tags: csharp
---

Note: This problem was taken from LeetCode - [Sort Colors](https://leetcode.com/problems/sort-colors/)

### Two Pointer Approach

Create two pointers one pointing to the start and the other pointing to the end of the array. Start checking from the beginning of the array, if you find a `zero`, swap it with the `zero pointer`. If you find a `two` then swap it with the `two pointer`. Keep doing this until the `two pointer` to get the required result.

```csharp
public void SortColors(int[] nums) {
    int zeroPt = 0;
    int twoPt = nums.Length - 1;
    
    int i = 0;
    
    while(i <= twoPt){
        if(nums[i] == 0){
            int temp = nums[i];
            nums[i] = nums[zeroPt];
            nums[zeroPt] = temp;
            zeroPt++;
            i++;
        }
        else if(nums[i] == 2){
            int temp = nums[i];
            nums[i] = nums[twoPt];
            nums[twoPt] = temp;
            twoPt--;
        }
        else{
            i++;
        }
    }
}
```

This solution has a time complexity of O(n) and space complexity of O(1).
