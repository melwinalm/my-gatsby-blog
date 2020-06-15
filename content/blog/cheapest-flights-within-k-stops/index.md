---
title: Cheapest Flights Within K Stops
date: "2020-06-15"
type: problem-solving
description: Cheapest Flights Within K Stops
tags: csharp
---

Note: This problem was taken from LeetCode - [Cheapest Flights Within K Stops](https://leetcode.com/problems/cheapest-flights-within-k-stops/)

### Using Depth First Search (Time Limit Exceeded)

```csharp
public int FindCheapestPrice(int n, int[][] flights, int src, int dst, int K) {
	int[,] graph = new int[n,n];
	
	foreach(int[] item in flights){
		int fNode = item[0];
		int tNode = item[1];
		int dist = item[2];
		
		graph[fNode, tNode] = dist;            
	}
	
	HashSet<int> visited = new HashSet<int>();
	
	int minDistance = this.DFS(src, dst, graph, visited, K+1, n);
	
	return minDistance == Int32.MinValue ? -1 : minDistance;
}

public int DFS(int fNode, int tNode, int[,] graph, HashSet<int> visited, int depth, int n){
	if(depth < 0){
		return -1;
	}
	
	if(fNode == tNode){
		return 0;
	}
	
	if(visited.Contains(fNode)){
		return -1;
	}
	
	visited.Add(fNode);
	
	int minDistance = Int32.MaxValue;

	for(int i = 0; i < n; i++){
		if(graph[fNode,i] != 0){
			int min = this.DFS(i, tNode, graph, visited, depth - 1, n);

			if(min == -1 || min == Int32.MaxValue){
				continue;
			}

			minDistance = Math.Min(minDistance, graph[fNode,i] + min);
		}
	}
	
	visited.Remove(fNode);
	
	return minDistance;
}
```

### Using Breadth First Search

```csharp
public int FindCheapestPrice(int n, int[][] flights, int src, int dst, int K) {
	Dictionary<int, List<int[]>> graph = new Dictionary<int, List<int[]>>();
	
	foreach(int[] item in flights){
		int fNode = item[0];
		int tNode = item[1];
		int dist = item[2];
		
		if(!graph.ContainsKey(fNode)){
			graph.Add(fNode, new List<int[]>(){new int[]{tNode, dist}});
		}
		else{
			graph[fNode].Add(new int[]{tNode, dist});
		}
	}
	
	int minCost = Int32.MaxValue;
	Queue<int[]> bfsQueue = new Queue<int[]>();
	
	bfsQueue.Enqueue(new int[]{src,0});
	
	int level = 0;
	
	while(bfsQueue.Any() && level <= K+1){
		int size = bfsQueue.Count;
		
		for(int i = 0; i < size; i++){
			var tempNode = bfsQueue.Dequeue();
			int toNode = tempNode[0];
			int toDistance = tempNode[1];
			
			if(toNode == dst){
				minCost = Math.Min(minCost, toDistance);
			}                
			
			// Checking if the to node exists in the graph
			if(!graph.ContainsKey(toNode)){
				continue;
			}
			
			foreach(int[] toCityNode in graph[toNode]){
				// Don't consider that path if the distance is already greater than minCost; 
				if(toDistance + toCityNode[1] > minCost){
					continue;
				}
				
				bfsQueue.Enqueue(new int[]{toCityNode[0], toDistance + toCityNode[1]});
			}
		}
		
		level++;
	}
	
	return minCost == Int32.MaxValue ? -1 : minCost;        
}
```
