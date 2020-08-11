---
title: Maximum Product of Three Numbers
date: "2020-08-11"
type: problem-solving
description: Maximum Product of Three Numbers
tags: csharp
---

Note: This problem was taken from LeetCode - [Maximum Product of Three Numbers](https://leetcode.com/problems/maximum-product-of-three-numbers/)

### Using Sorting

```csharp
public int MaximumProduct(int[] nums) {
	if(nums.Length < 3){
		return 0;
	}
	
	Array.Sort(nums);
	int N = nums.Length;
	
	return Math.Max(nums[N-1] * nums[N-2] * nums[N-3], nums[0] * nums[1] * nums[N-1]);
}
```
