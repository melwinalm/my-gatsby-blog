---
title: Minimum Number of Arrows to Burst Balloons
date: "2020-08-25"
type: problem-solving
description: Minimum Number of Arrows to Burst Balloons
tags: csharp
---

Note: This problem was taken from LeetCode - [Minimum Number of Arrows to Burst Balloons](https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/)

### Greedy Approach

```csharp
public int FindMinArrowShots(int[][] points) {
	if(points.Length == 0){
		return 0;
	}
	
	Array.Sort(points, (a,b)=>a[1]-b[1]);
		
	int currPoint = points[0][1];
	int count = 1;
	
	for(int i = 1; i < points.Length; i++){
		if(currPoint >= points[i][0]){
			continue;
		}
		
		count++;
		currPoint = points[i][1];
	}
		
	return count;
}
```
