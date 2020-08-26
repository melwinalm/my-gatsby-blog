---
title: Maximum Product Subarray
date: "2020-08-26"
type: problem-solving
description: Maximum Product Subarray
tags: csharp
---

Note: This problem was taken from LeetCode - [Maximum Product Subarray](https://leetcode.com/problems/maximum-product-subarray/)

### Greedy Approach

```csharp
public int MaxProduct(int[] nums) {
	if(nums.Length == 0){
		return 0;
	}
	
	int min = nums[0];
	int max = nums[0];
	int maxSoFar = nums[0];
	
	for(int i = 1; i < nums.Length; i++){
		
		if(nums[i] < 0){
			int temp = min;
			min = max;
			max = temp;
		}
		
		min = Math.Min(nums[i], min * nums[i]);
		max = Math.Max(nums[i], max * nums[i]);
		
		maxSoFar = Math.Max(maxSoFar, max);
	}
	
	return maxSoFar;
}
```
