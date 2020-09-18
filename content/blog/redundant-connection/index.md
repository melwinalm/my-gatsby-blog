---
title: Redundant Connection
date: "2020-09-18"
type: problem-solving
description: Redundant Connection
tags: csharp
---

Note: This problem was taken from LeetCode - [Redundant Connection](https://leetcode.com/problems/redundant-connection/)

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
