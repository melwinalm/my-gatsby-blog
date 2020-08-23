---
title: Most Visited Sector in a Circular Track
date: "2020-08-23"
type: problem-solving
description: Most Visited Sector in a Circular Track
tags: csharp
---

Note: This problem was taken from LeetCode - [Most Visited Sector in a Circular Track](https://leetcode.com/problems/most-visited-sector-in-a-circular-track/)

### Naive Approach

```csharp
public IList<int> MostVisited(int n, int[] rounds) {
	if(rounds.Length == 0){
		return new List<int>();
	}
	
	Dictionary<int, int> map = new Dictionary<int, int>();
	
	for(int i = 1; i <= n; i++){
		map[i] = 0;
	}
	
	int currSector = rounds[0];
	map[currSector] = 1;
	for(int i = 1; i < rounds.Length; i++){
		this.AddCounts(map, currSector, rounds[i], n);
		currSector = rounds[i];
	}
	
	int maxCount = 0;
	foreach(var item in map){
		maxCount = Math.Max(maxCount, item.Value);
	}
	
	List<int> output = new List<int>();
	foreach(var item in map){
		if(item.Value == maxCount){
			output.Add(item.Key);
		}
	}
	
	return output;        
}

public void AddCounts(Dictionary<int,int> map, int start, int end, int n){
	if(start <= end){
		for(int i = start+1; i<=end; i++){
			map[i] += 1;
		}
	}
	else{
		for(int i = start+1; i <= n; i++){
			map[i] += 1;
		}
		for(int i = 1; i <= end; i++){
			map[i] += 1;
		}
	}
}
```
