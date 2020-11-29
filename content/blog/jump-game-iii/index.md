---
title: Jump Game III
date: "2020-11-29"
type: problem-solving
description: Jump Game III
tags: csharp
---

Note: This problem was taken from LeetCode - [Jump Game III](https://leetcode.com/problems/jump-game-iii/)

### Using DFS

```csharp
public bool CanReach(int[] arr, int start) {
	HashSet<int> visited = new HashSet<int>();
	
	return this.DFS(arr, start, visited);
}

public bool DFS(int[] arr, int index, HashSet<int> visited){
	if(index < 0 || index >= arr.Length || visited.Contains(index)){
		return false;
	}
	
	if(arr[index] == 0){
		return true;
	}
	
	visited.Add(index);
	
	return this.DFS(arr, index + arr[index], visited) || this.DFS(arr, index - arr[index], visited);
}
```
