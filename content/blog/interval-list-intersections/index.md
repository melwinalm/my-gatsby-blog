---
title: Interval List Intersections
date: "2020-05-23"
type: problem-solving
description: Interval List Intersections
tags: csharp
---

Note: This problem was taken from LeetCode - [Interval List Intersections](https://leetcode.com/problems/interval-list-intersections/)

### Using Iteration

```csharp
public int[][] IntervalIntersection(int[][] A, int[][] B) {
	List<int[]> output = new List<int[]>();
	
	int i = 0;
	int j = 0;
	
	while(i < A.Length && j < B.Length){
		int start = Math.Max(A[i][0], B[j][0]);
		int end = Math.Min(A[i][1], B[j][1]);
		
		if(start <= end){
			output.Add(new int[]{start, end});
		}
		
		if(A[i][1] < B[j][1]){
			i++;
		}
		else{
			j++;
		}
	}
	
	return output.ToArray();
}
```
