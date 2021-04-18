---
title: Maximum Ice Cream Bars
date: "2021-04-18"
type: problem-solving
description: Maximum Ice Cream Bars
tags: csharp
---

Note: This problem was taken from LeetCode - [Maximum Ice Cream Bars](https://leetcode.com/problems/maximum-ice-cream-bars/)

### Using Greedy Approach

```csharp
public int MaxIceCream(int[] costs, int coins) {
	Array.Sort(costs);
	
	int count = 0;
	
	foreach(int cost in costs){
		if(coins >= cost){
			count++;
			coins -= cost;
		}
		else{
			break;
		}
	}

	return count;
}
```
