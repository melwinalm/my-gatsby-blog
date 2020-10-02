---
title: Car Pooling
date: "2020-09-21"
type: problem-solving
description: Car Pooling
tags: csharp
---

Note: This problem was taken from LeetCode - [Car Pooling](https://leetcode.com/problems/car-pooling/)

### Using Prefix Sum

This method uses nested loops to find the frequency count of ranges.

```csharp
public bool CarPooling(int[][] trips, int capacity) {
	int N = trips.Length;
	
	int[] locs = new int[1001];
	
	for(int i = 0; i < N; i++){
		int start = trips[i][1];
		int end = trips[i][2];
		int size = trips[i][0];
		
		locs[start] += size;
		
		if(end < 1001){
			locs[end] -= size;
		}
	}
	
	int sum = 0;
	for(int i = 0; i < 1001; i++){
		locs[i] += sum;
		sum = locs[i];
		
		if(locs[i] > capacity){
			return false;
		}
	}
	
	return true;
}
```
