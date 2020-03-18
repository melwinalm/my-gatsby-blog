---
title: Maximum Subarray
date: "2020-03-18"
type: problem-solving
description: Maximum Subarray
tags: csharp
---

Note: This problem was taken from LeetCode - [Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)


### Using Dynamic Programming

```csharp
    public int MaxSubArray(int[] nums) {
        int[] dp = new int[nums.Length];
        int maxSum = nums[0];
        
        dp[0] = nums[0];
        
        for(int i = 1; i < nums.Length; i++){
            dp[i] = dp[i-1] > 0 ? dp[i-1] + nums[i] : nums[i];
            maxSum = Math.Max(dp[i], maxSum);
        }
        
        return maxSum;
    }
```

This solution has a time and space complexity of O(n).

### Better Solution

This approach is similar to the previous one, except that we avoid using a redundant array to store all the values. Instead, two variables are used to store the current max sum and the overall max sum.

```csharp
public int MaxSubArray(int[] nums) {
    int maxSum = nums[0];
    int currSum = nums[0];
    
    for(int i = 1; i < nums.Length; i++){
        currSum = Math.Max(currSum + nums[i], nums[i]);
        maxSum = Math.Max(currSum, maxSum);
    }
    
    return maxSum;
}
```

This has a time complexity of O(n) and space complexity of O(1).
