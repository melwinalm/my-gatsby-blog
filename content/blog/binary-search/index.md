---
title: Binary Search
date: "2020-05-20"
type: problem-solving
description: Binary Search
tags: csharp
---

Note: This problem was taken from LeetCode - [Binary Search](https://leetcode.com/problems/binary-search/)

### Using Binary Search

```csharp
public int Search(int[] nums, int target) {
	int low = 0;
	int high = nums.Length - 1;
	
	while(low <= high){
		int mid = low + ((high - low)/2);
		
		if(nums[mid] == target){
			return mid;
		}
		else if(nums[mid] < target){
			low = mid + 1;
		}
		else{
			high = mid - 1;
		}
	}
	
	return -1;
}
```
