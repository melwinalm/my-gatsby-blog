---
title: House Robber
date: "2020-06-18"
type: problem-solving
description: House Robber
tags: csharp
---

Note: This problem was taken from LeetCode - [House Robber](https://leetcode.com/problems/house-robber/)

### Using Top Down Approach

```csharp
public int Rob(int[] nums) {
	Dictionary<int,int> memo = new Dictionary<int,int>();
	return this.MaxRob(nums, 0, memo);
}

public int MaxRob(int[] nums, int index, Dictionary<int,int> memo){
	if(index >= nums.Length){
		return 0;
	}
	
	if(memo.ContainsKey(index)){
		return memo[index];
	}

	memo[index] = Math.Max(nums[index] + this.MaxRob(nums, index + 2, memo), this.MaxRob(nums, index + 1, memo));

	return memo[index];
}
```

### Using Bottom Up Approach

```csharp
public int Rob(int[] nums) {
	int N = nums.Length;
	
	if(N == 0){
		return 0;
	}
	
	int[] dp = new int[N+1];
	
	dp[0] = 0;
	dp[1] = nums[0];
	
	for(int i = 1; i < N; i++){
		dp[i+1] = Math.Max(dp[i], dp[i-1] + nums[i]);
	}
	
	return dp[N];
}
```
