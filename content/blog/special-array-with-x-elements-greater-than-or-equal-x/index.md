---
title: Special Array With X Elements Greater Than or Equal X
date: "2020-10-04"
type: problem-solving
description: Special Array With X Elements Greater Than or Equal X
tags: csharp
---

Note: This problem was taken from LeetCode - [Special Array With X Elements Greater Than or Equal X](https://leetcode.com/problems/special-array-with-x-elements-greater-than-or-equal-x/)

### Naive Approach

```csharp
public int SpecialArray(int[] nums) {
	Array.Sort(nums);
	
	int N = nums.Length;
	
	for(int i = 0; i < N; i++){
		int remNum = N - i;
		
		if(nums[i] >= remNum && (i-1 < 0 || remNum > nums[i-1])){
			return remNum;
		}
	}
	
	return -1;
}
```
