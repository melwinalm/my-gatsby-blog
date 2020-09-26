---
title: Teemo Attacking
date: "2020-08-26"
type: problem-solving
description: Teemo Attacking
tags: csharp
---

Note: This problem was taken from LeetCode - [Teemo Attacking](https://leetcode.com/problems/teemo-attacking/)

### Using Merge Interval

```csharp
public int FindPoisonedDuration(int[] timeSeries, int duration) {
	int N = timeSeries.Length;
	
	if(N == 0){
		return 0;
	}
	
	int total = 0;
	
	for(int i = 0; i < N-1; i++){
		total += Math.Min(timeSeries[i+1] - timeSeries[i], duration);
	}
	
	return total + duration;
}
```
