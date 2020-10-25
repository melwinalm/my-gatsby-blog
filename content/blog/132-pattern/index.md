---
title: 132 Pattern
date: "2020-10-24"
type: problem-solving
description: 132 Pattern
tags: csharp
---

Note: This problem was taken from LeetCode - [132 Pattern](https://leetcode.com/problems/132-pattern/)

### Brute Force (Time Limit Exceeded Error)

```csharp
public bool Find132pattern(int[] nums) {
	if(nums.Length < 3){
		return false;
	}
	
	for(int i = 0; i < nums.Length; i++){
		for(int j = i+1; j < nums.Length; j++){
			for(int k = j+1; k < nums.Length; k++){
				if(nums[k] > nums[i] && nums[j] > nums[k]){
					return true;
				}
			}
		}
	}
	
	return false;
}
```
