---
title: Jump Game
date: "2020-05-28"
type: problem-solving
description: Jump Game
tags: csharp
---

Note: This problem was taken from LeetCode - [Possible Bipartition](https://leetcode.com/problems/jump-game/)

### Greedy Approach

```csharp
public bool CanJump(int[] nums) {
	int last = nums.Length - 1;
	
	for(int i = nums.Length - 1; i >= 0; i--){
		if(i + nums[i] >= last){
			last = i;
		}
	}
	
	return last == 0;
}
```
