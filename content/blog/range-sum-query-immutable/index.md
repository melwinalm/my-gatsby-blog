---
title: Range Sum Query - Immutable
date: "2020-05-09"
type: problem-solving
description: Range Sum Query - Immutable
tags: csharp
---

Note: This problem was taken from LeetCode - [Range Sum Query - Immutable](https://leetcode.com/problems/range-sum-query-immutable/)

### Using Cumulative Sum

```csharp
int[] cumulativeSum;
public NumArray(int[] nums) {
	cumulativeSum = new int[nums.Length + 1];
	cumulativeSum[0] = 0;
	
	for(int i = 0; i < nums.Length; i++){
		cumulativeSum[i+1] = cumulativeSum[i] + nums[i];
	}
}

public int SumRange(int i, int j) {
	return cumulativeSum[j+1] - cumulativeSum[i];
}
```
