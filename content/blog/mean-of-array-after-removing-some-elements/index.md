---
title: Mean of Array After Removing Some Elements
date: "2020-10-18"
type: problem-solving
description: Mean of Array After Removing Some Elements
tags: csharp
---

Note: This problem was taken from LeetCode - [Mean of Array After Removing Some Elements](https://leetcode.com/problems/mean-of-array-after-removing-some-elements/)

### Naive Solution

```csharp
public double TrimMean(int[] arr) {
	Array.Sort(arr);
	
	int size = arr.Length / 20;
	
	int sum = 0;
	int n = 0;
	
	for(int i = size; i < arr.Length - size; i++){
		sum += arr[i];
		n++;
	}
	
	double mean = (double)sum / (double)n;     
	return mean;
}
```
