---
title: Minimum Operations to Make Array Equal
date: "2021-04-07"
type: problem-solving
description: Minimum Operations to Make Array Equal
tags: csharp
---

Note: This problem was taken from LeetCode - [Minimum Operations to Make Array Equal](https://leetcode.com/problems/minimum-operations-to-make-array-equal/)

### Using Math

```csharp
public int MinOperations(int n) {
	if(n % 2 == 0){
		int mid = n/2;
		return mid * mid;
	}
	else{
		int mid = (n-1)/2;
		return mid * (mid+1);
	}
}
```
