---
title: Jump Game II
date: "2021-05-06"
type: problem-solving
description: Jump Game II
tags: csharp
---

Note: This problem was taken from LeetCode - [Jump Game II](https://leetcode.com/problems/jump-game-ii/submissions/)

### Using Greedy Approach

```csharp
public int Jump(int[] nums) {
	int count = 0;
	int currEnd = 0;
	int currMax = 0;
	
	for(int i = 0; i < nums.Length - 1; i++){
		currMax = Math.Max(currMax, i + nums[i]);
		if(i == currEnd){
			count++;
			currEnd = currMax;
		}
	}
	
	return count;
}
```
