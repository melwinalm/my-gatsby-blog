---
title: Two Sum II - Input array is sorted
date: "2020-08-18"
type: problem-solving
description: Two Sum II - Input array is sorted
tags: csharp
---

Note: This problem was taken from LeetCode - [Two Sum II - Input array is sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)

### Two Pointer Approach

```csharp
public int[] TwoSum(int[] numbers, int target) {
	int index1 = 0;
	int index2 = numbers.Length - 1;
	
	while(index1 < index2){
		int temp = numbers[index1] + numbers[index2];
		if(temp == target){
			break;
		}
		else if(temp < target){
			index1++;
		}
		else{
			index2--;
		}
	}
	
	return new int[]{index1+1, index2+1};
}
```
