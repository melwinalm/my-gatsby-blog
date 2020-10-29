---
title: Maximize Distance to Closest Person
date: "2020-10-29"
type: problem-solving
description: Maximize Distance to Closest Person
tags: csharp
---

Note: This problem was taken from LeetCode - [Maximize Distance to Closest Person](https://leetcode.com/problems/maximize-distance-to-closest-person/)

### One Pass Approach

```csharp
public int MaxDistToClosest(int[] seats) {
	int N = seats.Length;
	
	int start = -1;
	int result = 0;
	
	for(int i = 0; i < N; i++){
		if(seats[i] == 1){
			if(start == -1){
				result = Math.Max(result, i);
			}
			
			result = Math.Max(result, (i - start)/2);
			start = i;
		}
	}
	
	result = Math.Max(result, N - start - 1);
	
	return result;
}
```
