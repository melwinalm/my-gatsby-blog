---
title: Search in Rotated Sorted Array
date: "2020-04-19"
type: problem-solving
description: Search in Rotated Sorted Array
tags: csharp
---

Note: This problem was taken from LeetCode - [Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/)

### Binary Search

First find the index where the array starts i.e the smallest element in the array. Then perform a typical binary search but with respect to the actual lowest index instead of 0th index.

```csharp
public int Search(int[] nums, int target) {
	int n = nums.Length;
	
	// Find min element
	int low = 0;
	int high = n - 1;
	
	while(low < high){
		int mid = low + ((high - low)/2);
		if(nums[mid] > nums[high]){
			low = mid + 1;
		}
		else{
			high = mid;
		}
	}
	
	// Perform relative binary search
	int startIndex = low;
	low = 0;
	high = n - 1;
	
	while(low <= high){
		int mid = low + ((high - low)/2);
		int relativeMid = (mid + startIndex) % n;
		
		if(nums[relativeMid] == target){
			return relativeMid;
		}
		else if(nums[relativeMid] < target){
			low = mid + 1;
		}
		else{
			high = mid - 1;
		}
	}
	
	return -1;
}
```
