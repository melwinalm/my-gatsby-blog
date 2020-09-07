---
title: Minimum Deletion Cost to Avoid Repeating Letters
date: "2020-09-07"
type: problem-solving
description: Minimum Deletion Cost to Avoid Repeating Letters
tags: csharp
---

Note: This problem was taken from LeetCode - [Minimum Deletion Cost to Avoid Repeating Letters](https://leetcode.com/problems/minimum-deletion-cost-to-avoid-repeating-letters/)

### Naive Approach

```minCost += (group sum of repeated characters) - (max number in that group)```

```csharp
public int MinCost(string s, int[] cost) {
	int minCost = 0;
	
	int groupSum = cost[0];
	int groupMax = cost[0];
	for(int i = 1; i < s.Length; i++){
		if(s[i] == s[i-1]){
			groupMax = Math.Max(groupMax, cost[i]);
			groupSum += cost[i];
		}
		else{
			minCost += groupSum - groupMax;
			groupMax = cost[i];
			groupSum = cost[i];
		}
	}
	
	minCost += groupSum - groupMax; // To add the min cost if the group is part of last set of repeated characters
	
	return minCost;
}
```
