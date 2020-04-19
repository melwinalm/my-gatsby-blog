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
	int low = 0;
	int high = nums.Length - 1;
	
	while(low < high){
		int mid = (low + high)/2;
		
		if(nums[mid] > nums[high]){
			low = mid + 1;
		}
		else{
			high = mid;
		}
	}
	
	int rot = low;
	low = 0;
	high = nums.Length - 1;
	
	while(low <= high){
		int mid = (low+high)/2;
		int realMid = (rot + mid) % nums.Length;
		
		if(nums[realMid] == target){
			return realMid;
		}
		else if(nums[realMid] < target){
			low = mid + 1;
		}
		else{
			high = mid-1;
		}
	}
	
	return -1;
}
```
