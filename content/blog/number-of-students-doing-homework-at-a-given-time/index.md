---
title: Number of Students Doing Homework at a Given Time
date: "2020-05-17"
type: problem-solving
description: Number of Students Doing Homework at a Given Time
tags: csharp
---

Note: This problem was taken from LeetCode - [Number of Students Doing Homework at a Given Time](https://leetcode.com/problems/number-of-students-doing-homework-at-a-given-time/)

### Linear Scan

```csharp
public int BusyStudent(int[] startTime, int[] endTime, int queryTime) {
	int count = 0;
	
	for(int i = 0; i < startTime.Length; i++){
		if(startTime[i] <= queryTime && endTime[i] >= queryTime){
			count++;
		}
	}
	
	return count;
}
```
