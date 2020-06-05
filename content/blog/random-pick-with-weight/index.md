---
title: Random Pick with Weight
date: "2020-06-05"
type: problem-solving
description: Random Pick with Weight
tags: csharp
---

Note: This problem was taken from LeetCode - [Random Pick with Weight](https://leetcode.com/problems/random-pick-with-weight/)

### Using Cumulative Sum

```csharp
Random random;
int[] cumWeight;
int N;
public Solution(int[] w) {
	N = w.Length;
	random = new Random();
	cumWeight = new int[N];
	cumWeight[0] = w[0];
	
	for(int i = 1; i < N; i++){
		cumWeight[i] = cumWeight[i-1] + w[i];
	}
}

public int PickIndex() {
	int index = random.Next(0, this.cumWeight[N-1]) + 1;
	int res = Array.BinarySearch(this.cumWeight, index);
	return res >= 0 ? res : -res-1;
}
```
