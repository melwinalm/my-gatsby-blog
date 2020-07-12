---
title: Number of Good Pairs
date: "2020-07-12"
type: problem-solving
description: Number of Good Pairs
tags: csharp
---

Note: This problem was taken from LeetCode - [Number of Good Pairs](https://leetcode.com/problems/number-of-good-pairs/)

### Using Naive Approach

```csharp
public int NumIdenticalPairs(int[] nums) {
	int count = 0;
	
	for(int i = 0; i < nums.Length; i++){
		for(int j = i+1; j < nums.Length; j++){
			if(nums[i] == nums[j]){
				count++;
			}
		}
	}
	
	return count;
}
```

### Using Sorting

```csharp
public int NumIdenticalPairs(int[] nums) {
	int count = 0;
	int i = 0;
	Array.Sort(nums);
	
	for(int j = 1; j < nums.Length; j++){
		if(nums[j] == nums[i]){
			count += j - i;
		}
		else{
			i = j;
		}
	}
	
	return count;
}
```
