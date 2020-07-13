---
title: Path with Maximum Probability
date: "2020-07-12"
type: problem-solving
description: Path with Maximum Probability
tags: csharp
---

Note: This problem was taken from LeetCode - [Path with Maximum Probability](https://leetcode.com/problems/path-with-maximum-probability/)

### Using DFS (Time Limit Exceeded error)

```csharp
public double MaxProbability(int n, int[][] edges, double[] succProb, int start, int end) {
	Dictionary<int, List<Tuple<int, double>>> map = new Dictionary<int, List<Tuple<int, double>>>();
	
	for(int i = 0; i < n; i++){
		map[i] = new List<Tuple<int, double>>();
	}
	
	for(int i = 0; i < edges.Length; i++){
		int a = edges[i][0];
		int b = edges[i][1];
		double succ = succProb[i];
		
		map[a].Add(new Tuple<int,double>(b,succ));
		map[b].Add(new Tuple<int,double>(a,succ));
	}        
	
	HashSet<int> visited = new HashSet<int>();
	
	double maxCount = 0;
	
	this.DFS(start, end, visited, map, ref maxCount, 1, succProb);
	
	return maxCount;
}

public void DFS(int start, int end, HashSet<int> visited,  Dictionary<int, List<Tuple<int, double>>> map, ref double maxCount, double currCount, double[] succProb){
	if(start == end){
		maxCount = Math.Max(maxCount, currCount);
	}
	
	if(currCount <= maxCount){
		return;
	}
	
	if(visited.Contains(start)){
		return;
	}
	
	visited.Add(start);
	
	foreach(var item in map[start]){
		double temp = currCount*item.Item2;
		if(temp <= maxCount || visited.Contains(item.Item1)){
			continue;
		}
		
		this.DFS(item.Item1, end, visited, map, ref maxCount, temp, succProb);
	}
	
	visited.Remove(start);
}
```