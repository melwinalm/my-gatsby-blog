---
title: Maximum Number of Coins You Can Get
date: "2020-08-23"
type: problem-solving
description: Maximum Number of Coins You Can Get
tags: csharp
---

Note: This problem was taken from LeetCode - [Maximum Number of Coins You Can Get](https://leetcode.com/problems/maximum-number-of-coins-you-can-get/)

### Greedy Approach

```csharp
public int MaxCoins(int[] piles) {
	int n = piles.Length / 3;
	
	Array.Sort(piles);
	Array.Reverse(piles);
	
	int maxCoins = 0;
	
	for(int i = 0; i < n; i++){
		maxCoins += piles[(i*2) + 1];
	}
	
	return maxCoins;
}
```
