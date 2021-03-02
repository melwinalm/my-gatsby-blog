---
title: Distribute Candies
date: "2021-03-02"
type: problem-solving
description: Distribute Candies
tags: csharp
---

Note: This problem was taken from LeetCode - [Distribute Candies](https://leetcode.com/problems/distribute-candies/)

### Using Set

```csharp
public int DistributeCandies(int[] candyType) {
	HashSet<int> set = new HashSet<int>();
	
	foreach(int item in candyType){
		set.Add(item);
	}
	
	return Math.Min(set.Count, candyType.Length/2);
}
```
