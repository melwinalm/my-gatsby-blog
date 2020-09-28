---
title: Subarray Product Less Than K
date: "2020-09-28"
type: problem-solving
description: Subarray Product Less Than K
tags: csharp
---

Note: This problem was taken from LeetCode - [Subarray Product Less Than K](https://leetcode.com/problems/subarray-product-less-than-k/)

### Using Two Pointer Approach

```csharp
public int NumSubarrayProductLessThanK(int[] nums, int k) {
	if(k <= 1){
		return 0;
	}
	
	int N = nums.Length;
	
	int count = 0;
	
	int sIndex = 0;
	int eIndex = 0;
	
	int currProd = 1;
	
	while(eIndex < N){
		currProd *= nums[eIndex];
		
		while(currProd >= k){
			currProd /= nums[sIndex];
			sIndex++;
		}
		
		count += eIndex - sIndex + 1;
		
		eIndex++;
	}
	
	return count;
}
```
