---
title: Find Pivot Index
date: "2020-10-29"
type: problem-solving
description: Find Pivot Index
tags: csharp
---

Note: This problem was taken from LeetCode - [Find Pivot Index](https://leetcode.com/problems/find-pivot-index/)

### Prefix Sum

```csharp
public int PivotIndex(int[] nums) {
	int N = nums.Length;
	
	if(N == 0){
		return -1;
	}
	
	int[] leftSum = new int[N];
	int[] rightSum = new int[N];
	
	leftSum[0] = nums[0];
	rightSum[N-1] = nums[N-1];
	
	for(int i = 1; i < N; i++){
		leftSum[i] = leftSum[i-1] + nums[i];
	}
	
	for(int i = N-2; i >= 0; i--){
		rightSum[i] = rightSum[i+1] + nums[i];
	}
	
	for(int i = 0; i < N; i++){
		if(leftSum[i] == rightSum[i]){
			return i;
		}
	}
	
	return -1;
}
```
