---
title: Minimum Initial Energy to Finish Tasks
date: "2020-11-23"
type: problem-solving
description: Minimum Initial Energy to Finish Tasks
tags: csharp
---

Note: This problem was taken from LeetCode - [Minimum Initial Energy to Finish Tasks](https://leetcode.com/problems/minimum-initial-energy-to-finish-tasks/)

### Greedy Approach

```csharp
public int MinimumEffort(int[][] tasks) {
	Array.Sort(tasks, (a,b) => (a[1] - a[0]) - (b[1] - b[0]));
	
	int output = 0;
	
	foreach(int[] task in tasks){
		output = Math.Max(output + task[0], task[1]);
	}
	
	return output;
}
```
