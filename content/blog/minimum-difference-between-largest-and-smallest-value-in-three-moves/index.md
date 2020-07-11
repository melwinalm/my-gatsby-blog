---
title: Minimum Difference Between Largest and Smallest Value in Three Moves
date: "2020-07-12"
type: problem-solving
description: Minimum Difference Between Largest and Smallest Value in Three Moves
tags: csharp
---

Note: This problem was taken from LeetCode - [Minimum Difference Between Largest and Smallest Value in Three Moves](https://leetcode.com/problems/minimum-difference-between-largest-and-smallest-value-in-three-moves/)

```csharp
public int MinDifference(int[] nums) {
	int N = nums.Length;
	
	// For arrays of size less than or equal to 4, all elements can be made identical in 3 moves, so the min difference will always be zero.
	if(N <= 4){
		return 0;
	}
	
	Array.Sort(nums);
	
	int minValue = Int32.MaxValue;
	
	int totalMoves = 3;
	int currMove = 0;
	
	while(currMove <= totalMoves){
		minValue = Math.Min(minValue, nums[N-totalMoves+currMove-1] - nums[currMove]);
		
		currMove++;
	}

	return minValue;
}
```
