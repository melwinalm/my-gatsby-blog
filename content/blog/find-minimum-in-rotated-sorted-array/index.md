---
title: Find Minimum in Rotated Sorted Array
date: "2020-04-19"
type: problem-solving
description: Find Minimum in Rotated Sorted Array
tags: csharp
---

Note: This problem was taken from LeetCode - [Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)

### Binary Search

```csharp
public int FindMin(int[] nums) {
	int low = 0;
	int high = nums.Length - 1;
	
	while(low < high){
		int mid = (low + high)/2;
		// If mid is greater than high then a solution lies in te right half of section
		if(nums[mid] > nums[high]){
			low = mid + 1;
		}
		else{
			high = mid;
		}
	}
	
	return nums[low];
}
```
