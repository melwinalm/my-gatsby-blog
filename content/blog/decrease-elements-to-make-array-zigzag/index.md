---
title: Decrease Elements To Make Array Zigzag
date: "2020-08-21"
type: problem-solving
description: Decrease Elements To Make Array Zigzag
tags: csharp
---

Note: This problem was taken from LeetCode - [Decrease Elements To Make Array Zigzag](https://leetcode.com/problems/decrease-elements-to-make-array-zigzag/)

### Intuitive Approach

```csharp
public int MovesToMakeZigzag(int[] nums) {
	int n = nums.Length;
	if(n <= 1){
		return 0;
	}

	int even = 0;
	int odd = 0;
	
	// Finding the amount by which odd indices should be updated to match the given condition
	// For odd indices
	for(int i = 1; i < n; i+=2){
		int min = Math.Min(nums[i-1], i+1 < n ? nums[i+1] : Int32.MaxValue);
		
		if(min <= nums[i]){
			odd += (nums[i] - min + 1);
		}
	}
	
	// Finding the amount by which even indices should be updated to match the given condition
	// For Even Indices
	for(int i = 0; i < n; i+=2){
		int min = Math.Min(i > 0 ? nums[i-1] : Int32.MaxValue, i+1 < n ? nums[i+1] : Int32.MaxValue);
		
		if(min <= nums[i]){
			even += (nums[i] - min + 1);
		}
	}
	
	// The minimum of odd and even will give the required result
	return Math.Min(even, odd);
}
```
