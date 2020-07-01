---
title: Arranging Coins
date: "2020-07-01"
type: problem-solving
description: Arranging Coins
tags: csharp
---

Note: This problem was taken from LeetCode - [Arranging Coins](https://leetcode.com/problems/arranging-coins/)

### Using Loops

```csharp
public int ArrangeCoins(int n) {
	int count = 0;
	
	int stepSize = 1;
	while(n >= stepSize){
		count++;
		n -= stepSize;
		stepSize++;
	}
	
	return count;
}
```
