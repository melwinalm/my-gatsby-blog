---
title: Redundant Connection
date: "2020-09-18"
type: problem-solving
description: Redundant Connection
tags: csharp
---

Note: This problem was taken from LeetCode - [Redundant Connection](https://leetcode.com/problems/redundant-connection/)

### Using DFS (Detecting cycles in the graph)

Before adding an edge to the graph, perform a DFS and check if there is a cycle in the graph. If there is a cycle save that edge in a temporary variable. Repeat this for all the edges to get the required solution.

```csharp
public int[] FindRedundantConnection(int[][] edges) {
	Dictionary<int, HashSet<int>> graph = new Dictionary<int, HashSet<int>>();
	
	int N = edges.Length; // Number of nodes
	
	for(int i = 1; i <= N; i++){
		graph[i] = new HashSet<int>();
	}
	
	int[] output = new int[2];
	
	foreach(int[] edge in edges){
		int u = edge[0];
		int v = edge[1];
		
		if(this.DFS(graph, u, v, new HashSet<int>())){
			output = edge;
		}
		
		graph[u].Add(v);
		graph[v].Add(u);
	}
	
	return output;
}

public bool DFS(Dictionary<int, HashSet<int>> graph, int u, int v, HashSet<int> visited){
	if(u == v){
		return true;
	}
	
	if(visited.Contains(u)){
		return false;
	}
	
	visited.Add(u);
	
	foreach(int node in graph[u]){
		bool flag = this.DFS(graph, node, v, visited);
		
		if(flag){
			return true;
		}
	}
	
	return false;
}
```

### Using Union Find (with Path Compression)

```csharp
public class Solution {
    public int[] FindRedundantConnection(int[][] edges) {
        int nodes = edges.Length;
        
        UnionFind uf = new UnionFind(nodes);
        
        foreach(int[] edge in edges){
            int u = edge[0] - 1; // Adjusting to 0-indexing
            int v = edge[1] - 1;
            
            if(!uf.Unionize(u, v)){
                return edge;
            }     
        }
        
        return new int[]{0, 0};
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
    
    public bool Unionize(int a, int b){
        int parentA = this.Find(a);
        int parentB = this.Find(b);
        
        if(parentA == parentB){
            return false;
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
        
        return true;
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
