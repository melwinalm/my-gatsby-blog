---
title: Find First and Last Position of Element in Sorted Array
date: "2020-05-20"
type: problem-solving
description: Find First and Last Position of Element in Sorted Array
tags: csharp
---

Note: This problem was taken from LeetCode - [Find First and Last Position of Element in Sorted Array](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)

### Linear Scan using two pointers

```csharp
    public int[] SearchRange(int[] nums, int target) {
        int start = 0;
        int end = nums.Length - 1;
        
        while(start <= end){
            if(nums[start] == target && nums[end] == target){
                return new int[]{start, end};
            }
            
            if(nums[start] != target){
                start++;
            }
            
            if(nums[end] != target){
                end--;
            }
        }
        
        return new int[]{-1, -1};
    }
```

### Using Binary Search

```csharp
public int[] SearchRange(int[] nums, int target) {
	int[] output = new int[] {-1, -1};
	
	if(nums.Length == 0){
		return output;
	}
	
	int first = this.FirstBinarySearch(nums, target);
	
	// Target element not found
	if(nums[first] != target){
		return output;
	}
	
	output[0] = first;
	output[1] = this.LastBinarySearch(nums, target);
	
	return output;
}

public int FirstBinarySearch(int[] nums, int target){
	int low = 0;
	int high = nums.Length - 1;
	
	int mid = 0;
	
	while(low < high){
		mid = low + ((high - low)/2);            
		if(nums[mid] < target){
			low = mid + 1;
		}
		else{
			high = mid;
		}
	}
	
	return low;
}

public int LastBinarySearch(int[] nums, int target){
	int low = 0;
	int high = nums.Length - 1;
	
	int mid = 0;
	
	while(low < high){
		mid = low + ((high - low)/2) + 1;
		if(nums[mid] > target){
			high = mid - 1;
		}
		else{
			low = mid;
		}
	}
	
	return high;
}
```
