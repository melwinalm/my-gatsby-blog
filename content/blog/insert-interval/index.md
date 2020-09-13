---
title: Insert Interval
date: "2020-09-13"
type: problem-solving
description: Insert Interval
tags: csharp
---

Note: This problem was taken from LeetCode - [Insert Interval](https://leetcode.com/problems/insert-interval/)

### Straight Forward Approach

```csharp
public int[][] Insert(int[][] intervals, int[] newInterval) {
	List<int[]> output = new List<int[]>();
	
	foreach(int[] interval in intervals){
		
		if(newInterval[0] > interval[1]){
			output.Add(interval);
		}
		else if(newInterval[1] < interval[0]){
			output.Add(newInterval);
			newInterval = interval;
		}
		else{
			newInterval[0] = Math.Min(interval[0], newInterval[0]);
			newInterval[1] = Math.Max(interval[1], newInterval[1]);
		}
	}
	
	output.Add(newInterval);
	
	return output.ToArray();
}
```
