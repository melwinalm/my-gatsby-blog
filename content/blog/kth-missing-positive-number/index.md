---
title: Kth Missing Positive Number
date: "2020-08-11"
type: problem-solving
description: Kth Missing Positive Number
tags: csharp
---

Note: This problem was taken from LeetCode - [Kth Missing Positive Number](https://leetcode.com/problems/kth-missing-positive-number/)

### Naive Solution

```csharp
public int FindKthPositive(int[] arr, int k) {
	int i = 1;
	int index = 0;
	while(k > 0 && index < arr.Length){
		if(i == arr[index]){
			index++;
		}
		else{
			k--;
		}
		i++;
	}
	
	return i + k - 1;
}
```
