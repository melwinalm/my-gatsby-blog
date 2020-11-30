---
title: Minimum Height Trees
date: "2020-11-30"
type: problem-solving
description: Minimum Height Trees
tags: csharp
---

Note: This problem was taken from LeetCode - [Minimum Height Trees](https://leetcode.com/problems/minimum-height-trees/)

### Topological Sorting

```csharp
public IList<int> FindMinHeightTrees(int n, int[][] edges) {
	List<int> output = new List<int>();
	
	if(n == 1){
		output.Add(0);
		return output;
	}
	
	int[] degree = new int[n];
	
	Dictionary<int, List<int>> map = new Dictionary<int, List<int>>();
	
	// Building graph using adjacency list
	foreach(int[] edge in edges){
		if(!map.ContainsKey(edge[0])){
			map[edge[0]] = new List<int>();
		}
		
		if(!map.ContainsKey(edge[1])){
			map[edge[1]] = new List<int>();
		}
		
		map[edge[0]].Add(edge[1]);
		map[edge[1]].Add(edge[0]);
		
		degree[edge[0]]++;
		degree[edge[1]]++;
	}

	Queue<int> bfsQueue = new Queue<int>();
	
	for(int i = 0; i < n; i++){
		if(degree[i] == 1){
			bfsQueue.Enqueue(i);
		}
	}
	
	while(bfsQueue.Count > 0){
		List<int> temp = new List<int>();
		int size = bfsQueue.Count;
		
		for(int i = 0; i < size; i++){
			int node = bfsQueue.Dequeue();
			temp.Add(node);
			
			foreach(int child in map[node]){
				degree[child]--;
				if(degree[child] == 1){
					bfsQueue.Enqueue(child);
				}
			}
			
			output = temp;
		}
	}
	
	return output;
}
```
