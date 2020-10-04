---
title: Remove Covered Intervals
date: "2020-10-04"
type: problem-solving
description: Remove Covered Intervals
tags: csharp
---

Note: This problem was taken from LeetCode - [Remove Covered Intervals](https://leetcode.com/problems/remove-covered-intervals/)

### Using Sorting + Greedy

```csharp
public int RemoveCoveredIntervals(int[][] intervals) {
	
	// Sort the intervals based on the the starting time. If starting times are same then sort them based on interval size. i.e if there's (1,2) and (1,4) then after sorting it should be (1,4), (1,2)
	Array.Sort(intervals, (a,b) => a[0] != b[0] ? a[0] - b[0] : (b[1] - b[0]) - (a[1] - a[0]));
	
	int count = intervals.Length;
	
	int[] curr = intervals[0];
	
	for(int i = 1; i < intervals.Length; i++){
		if(curr[0] <= intervals[i][0] && intervals[i][1] <= curr[1]){
			count--;
		}
		else{
			curr = intervals[i];
		}
	}
	
	return count;
}
```
