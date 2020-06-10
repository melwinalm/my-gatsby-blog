---
title: Search Insert Position
date: "2020-06-10"
type: problem-solving
description: Search Insert Position
tags: csharp
---

Note: This problem was taken from LeetCode - [Search Insert Position](https://leetcode.com/problems/search-insert-position/)

### Binary Search

```csharp
public int SearchInsert(int[] nums, int target) {
	int N = nums.Length;        
	int low = 0;
	int high = N - 1;
	
	while(low <= high){
		int mid = low + ((high - low)/ 2);
		
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
	
	return low;
}
```
