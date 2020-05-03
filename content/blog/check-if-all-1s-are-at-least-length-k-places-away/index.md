---
title: Check If All 1's Are at Least Length K Places Away
date: "2020-05-03"
type: problem-solving
description: Check If All 1's Are at Least Length K Places Away
tags: csharp
---

Note: This problem was taken from LeetCode - [Check If All 1's Are at Least Length K Places Away](https://leetcode.com/problems/check-if-all-1s-are-at-least-length-k-places-away/)

### Linear Scan

Simply perform a linear scan on the array. Whenever a `1` is found check if the next `k` items are not `1`. Repeat this throughout the array to get the result.

```csharp
    public bool KLengthApart(int[] nums, int k) {
        int i = 0;
        while(i < nums.Length){
            if(nums[i] == 1){
                int temp = i;
                for(int j = 1; j <= k; j++){
                    if(i+j < nums.Length && nums[i+j] == 1){
                        return false;
                    }
                    temp = i + j;
                }
                i = temp;
            }
            i++;
        }
        
        return true;
    }
```
