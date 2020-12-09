---
title: Pairs of Songs With Total Durations Divisible by 60
date: "2020-12-09"
type: problem-solving
description: Pairs of Songs With Total Durations Divisible by 60
tags: csharp
---

Note: This problem was taken from LeetCode - [Pairs of Songs With Total Durations Divisible by 60](https://leetcode.com/problems/pairs-of-songs-with-total-durations-divisible-by-60/)

### Two Sum Approach

```csharp
public int NumPairsDivisibleBy60(int[] time) {
	int[] mod = new int[60];
	
	int count = 0;
	
	foreach(int t in time){
		int sec = t % 60;
		count += mod[(60 - sec) % 60];
		mod[sec]++;
	}
	
	return count;
}
```
