---
title: Remove Duplicates from Sorted Array II
date: "2020-12-12"
type: problem-solving
description: Remove Duplicates from Sorted Array II
tags: csharp
---

Note: This problem was taken from LeetCode - [Binary Search Tree Iterator](https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/)

### Fast and Slow pointer

```csharp
public int RemoveDuplicates(int[] nums) {
	int N = nums.Length;
	
	if(N < 3){
		return N;
	}
	
	int slow = 2;
	int fast = 2;
	
	while(fast < N){
		if(nums[slow-2] != nums[fast]){
			nums[slow] = nums[fast];
			slow++;
		}
		fast++;
	}
	
	return slow;
}
```
