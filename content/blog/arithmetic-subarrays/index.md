---
title: Arithmetic Subarrays
date: "2020-10-25"
type: problem-solving
description: Arithmetic Subarrays
tags: csharp
---

Note: This problem was taken from LeetCode - [Arithmetic Subarrays](https://leetcode.com/problems/arithmetic-subarrays/)

### Naive Approach

```csharp
public IList<bool> CheckArithmeticSubarrays(int[] nums, int[] l, int[] r) {
	List<bool> output = new List<bool>();
	
	for(int i = 0; i < l.Length; i++){
		int[] newArray = this.SubArray(nums, l[i], r[i]);
		output.Add(this.IsArithmetic(newArray));
	}
	
	return output;
}

public int[] SubArray(int[] nums, int l, int r){
	int[] result = new int[r-l+1];
	
	Array.Copy(nums, l, result, 0, r-l+1);
	
	return result;
}

public bool IsArithmetic(int[] arr){
	if(arr.Length <= 2){
		return true;
	}
	
	Array.Sort(arr);
	
	int d = arr[1] - arr[0];
	
	for(int i = 2; i < arr.Length; i++){
		if(arr[i] - arr[i-1] != d){
			return false;
		}
	}
	
	return true;
}
```
