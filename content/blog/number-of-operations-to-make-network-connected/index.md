---
title: Number of Operations to Make Network Connected
date: "2020-09-17"
type: problem-solving
description: Number of Operations to Make Network Connected
tags: csharp
---

Note: This problem was taken from LeetCode - [Number of Operations to Make Network Connected](https://leetcode.com/problems/number-of-operations-to-make-network-connected/)

### Using Depth First Search

Find the number of connected components in the given graph. `count - 1` will be the number of edges that will have to be moved to make the network connected. Perform DFS on all the nodes. When a node is traversed mark it as visited. This should give us the result

```csharp
public int MakeConnected(int n, int[][] connections) {
	//There should be atleat n-1 edges in the graph to make the network connected
	if(connections.Length < n-1){
		return -1;
	}
	
	Dictionary<int, HashSet<int>> graph = new Dictionary<int, HashSet<int>>();
	
	for(int i = 0; i < n; i++){
		graph[i] = new HashSet<int>();
	}
	
	foreach(int[] edge in connections){
		int f = edge[0];
		int t = edge[1];
		
		graph[f].Add(t);
		graph[t].Add(f);
	}
	
	int connectedComponents = 0;
	
	bool[] visited = new bool[n];
	
	for(int i = 0; i < n; i++){
		if(visited[i]){
			continue;
		}
		
		connectedComponents++;
		
		this.DFS(graph, visited, i);
	}
	
	return connectedComponents - 1;
}

public void DFS(Dictionary<int, HashSet<int>> graph, bool[] visited, int currNode){
	if(visited[currNode]){
		return;
	}
	
	visited[currNode] = true;
	
	foreach(int toNode in graph[currNode]){
		this.DFS(graph, visited, toNode);
	}
}
```

### Union Find (with Path Compression)

```csharp
public class Solution {
    public int MakeConnected(int n, int[][] connections) {
        //There should be atleat n-1 edges in the graph to make the network connected
        if(connections.Length < n-1){
            return -1;
        }
        
        UnionFind uf = new UnionFind(n);
        
        foreach(int[] edge in connections){
            uf.Unionize(edge[0], edge[1]);
        }
        
        return uf.connectedComponents - 1;
    }
}

public class UnionFind{
    
    int[] weight;
    int[] parent;
    
    public int connectedComponents;
    
    public UnionFind(int n){
        weight = new int[n];        
        parent = new int[n];
        
        Array.Fill(weight, 1);
        
        for(int i = 0; i < n; i++){
            parent[i] = i;
        }
        
        connectedComponents = n;
    }
    
    public void Unionize(int a, int b){
        int parentA = this.Find(a);
        int parentB = this.Find(b);
        
        if(parentA == parentB){
            return;
        }
        
        if(weight[parentA] >= weight[parentB]){
            parent[parentB] = parentA;
            weight[parentA] += weight[parentB];
        }
        else{
            parent[parentA] = parentB;
            weight[parentB] += weight[parentA];
        }
        
        connectedComponents--;
    }
    
    public int Find(int a){
        
        int rootNode = a;
        
        while(rootNode != parent[rootNode]){
            rootNode = parent[rootNode];
        }
        
        // Applying path compression
        while(a != rootNode){
            int tempNode = parent[a];
            parent[a] = rootNode;
            a = tempNode;
        }
        
        return rootNode;
    }
}
```
