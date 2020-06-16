---
title: Running Sum of 1d Array
date: "2020-06-16"
type: problem-solving
description: Running Sum of 1d Array
tags: csharp
---

Note: This problem was taken from LeetCode - [Running Sum of 1d Array](https://leetcode.com/problems/running-sum-of-1d-array/)

### Using Prefix Sum

```csharp
public int[] RunningSum(int[] nums) {
	int N = nums.Length;
	
	int[] output = new int[N];
	
	if(N == 0){
		return output;
	}
	
	output[0] = nums[0];
	
	for(int i = 1; i < N; i++){
		output[i] = output[i-1] + nums[i];
	}
	
	return output;
}
```
