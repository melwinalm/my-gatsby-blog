---
title: Widest Vertical Area Between Two Points Containing No Points
date: "2020-10-31"
type: problem-solving
description: Widest Vertical Area Between Two Points Containing No Points
tags: csharp
---

Note: This problem was taken from LeetCode - [Widest Vertical Area Between Two Points Containing No Points](https://leetcode.com/problems/widest-vertical-area-between-two-points-containing-no-points/)

### Using Sorting

```csharp
public int MaxWidthOfVerticalArea(int[][] points) {
	Array.Sort(points, (a,b) => a[0] - b[0]);
	
	int maxSoFar = 0;
	
	for(int i = 1; i < points.Length; i++){
		maxSoFar = Math.Max(maxSoFar, points[i][0] - points[i-1][0]);
	}
	
	return maxSoFar;
}
```
