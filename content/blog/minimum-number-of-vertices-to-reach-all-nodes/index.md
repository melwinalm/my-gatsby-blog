---
title: Minimum Number of Vertices to Reach All Nodes :star:
date: "2020-08-23"
type: problem-solving
description: Minimum Number of Vertices to Reach All Nodes :star:
tags: csharp
---

Note: This problem was taken from LeetCode - [Minimum Number of Vertices to Reach All Nodes](https://leetcode.com/problems/minimum-number-of-vertices-to-reach-all-nodes/)

### In-Degree Nodes Approach

All the nodes which donot have any incoming edge is the solution for this method.

```csharp
public IList<int> FindSmallestSetOfVertices(int n, IList<IList<int>> edges) {
	HashSet<int> startNodes = new HashSet<int>();
	
	for(int i = 0 ; i < n; i++){
		startNodes.Add(i);
	}
	
	foreach(var item in edges){
		int to = item[1];            
		startNodes.Remove(to);
	}
	
	return startNodes.ToList();
}
```
