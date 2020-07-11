---
title: Range Sum of Sorted Subarray Sums
date: "2020-07-11"
type: problem-solving
description: Range Sum of Sorted Subarray Sums
tags: csharp
---

Note: This problem was taken from LeetCode - [Range Sum of Sorted Subarray Sums](https://leetcode.com/problems/range-sum-of-sorted-subarray-sums/)

### Using Prefix Sum

```csharp
public int RangeSum(int[] nums, int n, int left, int right) {
	List<int> perms = new List<int>();
	
	if(nums.Length == 0){
		return 0;
	}
	
	this.DP(nums, perms);
	perms.Sort();
	
	int output = 0;
	
	for(int i = left-1; i < right; i++){
		output += perms[i];
	}
	
	return output;
}

public void DP(int[] nums, List<int> perms){
	for(int i = 0; i < nums.Length; i++){
		int temp = 0;
		for(int j = i ; j < nums.Length; j++){
			temp += nums[j];
			perms.Add(temp);
		}
	}
}
```
