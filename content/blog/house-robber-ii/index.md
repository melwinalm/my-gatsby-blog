---
title: House Robber II
date: "2020-10-19"
type: problem-solving
description: House Robber II
tags: csharp
---

Note: This problem was taken from LeetCode - [House Robber II](https://leetcode.com/problems/house-robber-ii/)

### Using DP (Bottom Up Approach)

```csharp
public int Rob(int[] nums) {
	int N = nums.Length;
	
	if(N == 0){
		return 0;
	}
	else if(N < 2){
		return nums[0];
	}
	
	return Math.Max(this.DP(nums, 0, N-2), this.DP(nums, 1, N-1));
}

public int DP(int[] nums, int low, int high){
	int prev = 0;
	int curr = 0;
	
	for(int i = low; i <= high; i++){
		int temp = Math.Max(prev + nums[i], curr);
		prev = curr;
		curr = temp;
	}
	
	return curr;
}
```
