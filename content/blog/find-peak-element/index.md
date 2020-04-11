---
title: Find Peak Element
date: "2020-04-11"
type: problem-solving
description: Find Peak Element
tags: csharp
---

Note: This problem was taken from LeetCode - [Find Peak Element](https://leetcode.com/problems/find-peak-element/)

### Brute Force Approach

```csharp
public int FindPeakElement(int[] nums) {
	int n = nums.Length;
	if(n == 0){
		return 0;
	}
	else if(n == 1){
		return 0;
	}
	
	// Check if the first element is the peak element
	if(nums[0] > nums[1]){
		return 0;
	}
	
	// Check if the last element is the peak element
	if(nums[n-1] > nums[n-2]){
		return n - 1;
	}
	
	// Iteratively check all the elements in the array if it is a peak element.
	for(int i = 1; i < n-1; i++){
		if(nums[i] > nums[i-1] && nums[i] > nums[i+1]){
			return i;
		}
	} 
	
	return 0;
}
```

### Binary Search Approach

The Binary search algorithm is used mostly with the problems where the input array is sorted, but in this case, we know that the input array is not in a sorted format. But it works because, at a certain part of the array where peak element lies, that part will be in a sorted format. We use this property along with Binary search to find the peak element.

Consider the following example with the input array:
```
[5,6,4,3,2,9,3]
```
In the above example, the peak elements are 6 and 9.

Let's apply binary search on the array:

```
left: 0
right: 6
mid: 3
```
Check if `mid[3] < mid[4]`. In this scenario, yes it is. So this implies that there has to be a peak element in the right half of the array. Why is that?.
Consider the element mid[4], it's left element is lesser than it. And the right element can be either of the two:

- Higher than mid[4] - Then we repeat the same process, that is the right of mid[5] should have at least one peak element.
- Lower than mid[4]. If mid[5] is lower than mid[4] then mid[4] is the peak element.

Repeat this process by dividing the array into half on each traversal, and this will get you the required solution.

```csharp
public int FindPeakElement(int[] nums) {
	int left = 0;
	int right = nums.Length - 1;
	
	while(left < right){
		int mid = (left + right)/2;
		
		if(nums[mid] < nums[mid+1]){
			left = mid + 1;
		}
		else{
			right = mid;
		}
	}
	return left;
}
```

| Approach | Time Complexity | Space Complexity |
| ------------- |:-------------:| :-----:|
| Brute Force | O(n) | O(1) |
| Binary Search | O(log n) | O(1) |
