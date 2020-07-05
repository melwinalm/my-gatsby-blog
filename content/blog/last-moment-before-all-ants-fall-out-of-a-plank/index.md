---
title: Last Moment Before All Ants Fall Out of a Plank
date: "2020-07-05"
type: problem-solving
description: Last Moment Before All Ants Fall Out of a Plank
tags: csharp
---

Note: This problem was taken from LeetCode - [Last Moment Before All Ants Fall Out of a Plank](https://leetcode.com/problems/last-moment-before-all-ants-fall-out-of-a-plank/)

### Using Naive approach

When two ants meet at a point, it's same as these ants continuing to move in the same direction. So the time units required for all ants to fall off the plank will be the max of the left ants moving towards the start(i.e. 0) and right ants moving towards the end of the plank(i.e. n). 

```csharp
public int GetLastMoment(int n, int[] left, int[] right) {
	int max = 0;
	
	foreach(int item in left){
		max = Math.Max(max, item);
	}
	
	foreach(int item in right){
		max = Math.Max(max, n - item);
	}
	
	return max;
}
```
