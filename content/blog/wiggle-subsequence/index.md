---
title: Wiggle Subsequence
date: "2021-03-19"
type: problem-solving
description: Wiggle Subsequence
tags: csharp
---

Note: This problem was taken from LeetCode - [Wiggle Subsequence](https://leetcode.com/problems/wiggle-subsequence/)

### Dynamic Programming

```csharp
public int WiggleMaxLength(int[] nums) {
	if(nums.Length <= 1){
		return nums.Length;
	}
	
	int up = 1;
	int down = 1;
	
	for(int i = 0; i < nums.Length - 1; i++){
		if(nums[i] < nums[i+1]){ // uphill
			up = down + 1;   
		}
		else if(nums[i] > nums[i+1]){
			down = up + 1;
		}
	}
	
	return Math.Max(up, down);
}
```
