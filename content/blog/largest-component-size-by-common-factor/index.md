---
title: Largest Component Size by Common Factor
date: "2020-08-30"
type: problem-solving
description: Largest Component Size by Common Factor
tags: csharp
---

Note: This problem was taken from LeetCode - [Largest Component Size by Common Factor](https://leetcode.com/problems/largest-component-size-by-common-factor/)

### Adjacency List + DFS (Time Limit Exceeded error)

```csharp
public int LargestComponentSize(int[] A) {
	int n = A.Length;
	
	Dictionary<int, HashSet<int>> graph = new Dictionary<int, HashSet<int>>();
	
	foreach(int node in A){
		graph[node] = new HashSet<int>();
	}
	
	for(int i = 0; i < n; i++){
		for(int j = i+1; j < n; j++){
			if(this.GCD(A[i], A[j]) > 1){
				graph[A[i]].Add(A[j]);
				graph[A[j]].Add(A[i]);
			}
		}
	}
	
	HashSet<int> visited = new HashSet<int>();
	
	int maxSoFar = 0;
	
	foreach(var node in graph){
		if(!visited.Contains(node.Key)){
			maxSoFar = Math.Max(maxSoFar, this.DFS(graph, visited, node.Key));
		}
	}
	
	return maxSoFar;
}

public int GCD(int a, int b){
	if (b == 0){
	  return a;
	}
	return this.GCD(b, a % b);
}

public int DFS(Dictionary<int, HashSet<int>> graph, HashSet<int> visited, int node){
	if(visited.Contains(node)){
		return 0;
	}
	
	visited.Add(node);
	
	int count = 1;
	
	foreach(int currNode in graph[node]){
		count += this.DFS(graph, visited, currNode);
	}
	
	return count;
}
```

### Using Union Find

```csharp
public int LargestComponentSize(int[] A) {
	Dictionary<int, int> parent = new Dictionary<int,int>();
	
	foreach(int num in A){
		for(int factor = 2; factor*factor <= num; factor++){
			if(num % factor == 0){
				this.Unify(num, factor, parent);
				this.Unify(num, num/factor, parent);
			}
		}
	}
	
	Dictionary<int,int> freqCount = new Dictionary<int,int>();
	int maxSoFar = 1;
	foreach(int item in A){
		int p = this.Find(item, parent);
		if(freqCount.ContainsKey(p)){
			freqCount[p] += 1;
			maxSoFar = Math.Max(maxSoFar, freqCount[p]);
		}
		else{
			freqCount[p] = 1;
		}
	}
	
	return maxSoFar;
}

public void Unify(int a, int b, Dictionary<int,int> parents){
	int aParent = this.Find(a, parents);
	int bParent = this.Find(b, parents);
	
	if(aParent < bParent){
		parents[bParent] = aParent;
	}
	else{
		parents[aParent] = bParent;
	}
}

public int Find(int i, Dictionary<int,int> parent){
	if(!parent.ContainsKey(i)){
		parent[i] = i;
	}
	
	while(i != parent[i]){
		i = parent[i];
	}
	
	return i;
}
```
