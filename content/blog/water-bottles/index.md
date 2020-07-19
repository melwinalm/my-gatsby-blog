---
title: Water Bottles
date: "2020-07-19"
type: problem-solving
description: Water Bottles
tags: csharp
---

Note: This problem was taken from LeetCode - [Water Bottles](https://leetcode.com/problems/water-bottles/)

### Log N method

```csharp
public int NumWaterBottles(int numBottles, int numExchange) {
	int output = numBottles;
	int rem = numBottles;
	
	while(rem/numExchange > 0){
		output += (rem/numExchange);
		rem = rem -((rem/numExchange)*numExchange) + (rem/numExchange);
	}
	
	return output;
}
```
