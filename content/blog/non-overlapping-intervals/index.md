---
title: Non-overlapping Intervals
date: "2020-10-25"
type: problem-solving
description: Non-overlapping Intervals
tags: csharp
---

Note: This problem was taken from LeetCode - [Non-overlapping Intervals](https://leetcode.com/problems/non-overlapping-intervals/)

### Greedy Approach

```csharp
public int EraseOverlapIntervals(int[][] intervals) {
	int N = intervals.Length;
	
	if(N == 0){
		return 0;
	}
	
	Array.Sort(intervals, (a,b) => a[0] - b[0]);
	
	int result = 0;
	int minEnd = intervals[0][1];
	
	for(int i = 1; i < N; i++){
		int[] curr = intervals[i];
		
		if(minEnd > curr[0]){
			minEnd = Math.Min(minEnd, curr[1]);
			result++;
		}
		else{
			minEnd = curr[1];
		}
	}
	
	return result;        
}
```
