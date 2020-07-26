---
title: Count Odd Numbers in an Interval Range
date: "2020-07-26"
type: problem-solving
description: Count Odd Numbers in an Interval Range
tags: csharp
---

Note: This problem was taken from LeetCode - [Count Odd Numbers in an Interval Range](https://leetcode.com/problems/count-odd-numbers-in-an-interval-range/)

### Logical Approach

```csharp
public int CountOdds(int low, int high) {
	int lowMod = low%2;
	int highMod = high%2;
	
	if(lowMod == 0 && highMod == 0){
		return (high-low)/2;
	}
	else{
		return (high-low)/2 + 1; 
	}
}
```
