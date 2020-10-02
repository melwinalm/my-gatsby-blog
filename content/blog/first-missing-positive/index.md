---
title: First Missing Positive
date: "2020-10-01"
type: problem-solving
description: First Missing Positive
tags: csharp
---

Note: This problem was taken from LeetCode - [First Missing Positive](https://leetcode.com/problems/first-missing-positive/)

### O(n) time with O(1) space

```csharp
public int FirstMissingPositive(int[] nums) {
	int N = nums.Length;
	
	for(int i = 0; i < N; i++){
		while(nums[i] > 0 && nums[i] <= N && nums[nums[i]-1] != nums[i]){
			this.Swap(nums, i, nums[i]-1);
		}
	}
	
	for(int i = 0; i < N; i++){
		if(nums[i] != i+1){
			return i+1;
		}
	}
	
	return N+1;
}

public void Swap(int[] nums, int a, int b){
	int temp = nums[a];
	nums[a] = nums[b];
	nums[b] = temp;
}
```
