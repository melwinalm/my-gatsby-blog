---
title: Minimum Time Visiting All Points
date: "2020-06-16"
type: problem-solving
description: Minimum Time Visiting All Points
tags: csharp
---

Note: This problem was taken from LeetCode - [Minimum Time Visiting All Points](https://leetcode.com/problems/minimum-time-visiting-all-points/)

### Using Iteration

```csharp
public int MinTimeToVisitAllPoints(int[][] points) {
	if(points.Length == 0){
		return 0;
	}
	
	int output = 0;
	
	for(int i = 1; i < points.Length; i++){
		output += Math.Max(Math.Abs(points[i][0] - points[i-1][0]), Math.Abs(points[i][1] - points[i-1][1]));
	}
	
	return output;
}
```
