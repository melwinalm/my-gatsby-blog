---
title: Maximum Average Subarray I
date: "2020-01-17"
type: problem-solving
description: Maximum Average Subarray I
tags: csharp
---

Note: This problem was taken from LeetCode - [Maximum Average Subarray I](https://leetcode.com/problems/maximum-average-subarray-i/)

This problem can be solved using the Sliding Window Technique. See the below solution.

### Sliding Window Method

In this technique, first find the sum of k (i.e. window size) items in the input array, set it as the maxsum for now. Now find the sum by looping through the remaining elements in the array, that is adding the next element to the sliding window and remove the first element from the window. During this process, if the current sum is more than the max sum, then replace max sum with the current sum. Now at the end of the loop, you will have the maximum sum from the given array. Divide that number by the k which will give you maximum average.

```csharp
public double FindMaxAverage(int[] nums, int k) {
    int currSum = 0;
    int maxSum = 0;
    
    for(int i = 0; i< k; i++ ){
        currSum += nums[i];
    }
    maxSum = currSum;
    
    int startPointer = 0;
    int endPointer = k; 
    
    while(endPointer < nums.Length){
        currSum += nums[endPointer] - nums[startPointer];
        if(currSum > maxSum){
            maxSum = currSum;
        }
        endPointer++;
        startPointer++;
    }
    
    return (double)maxSum/k;
}
```
