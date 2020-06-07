---
title: Shuffle the Array
date: "2020-06-07"
type: problem-solving
description: Shuffle the Array
tags: csharp
---

Note: This problem was taken from LeetCode - [Shuffle the Array](https://leetcode.com/problems/shuffle-the-array/)

### Two Pointer Approach

```csharp
public int[] Shuffle(int[] nums, int n) {
	int fPointer = 0;
	int sPointer = n;
	
	int[] output = new int[2*n];
	
	int i = 0;
	while(fPointer < n){
		output[i] = nums[fPointer];
		output[i+1] = nums[sPointer];
		i += 2;
		fPointer++;
		sPointer++;
	}
	
	return output;
}
```
