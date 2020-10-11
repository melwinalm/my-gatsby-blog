---
title: Maximal Network Rank
date: "2020-10-11"
type: problem-solving
description: Maximal Network Rank
tags: csharp
---

Note: This problem was taken from LeetCode - [Maximal Network Rank](https://leetcode.com/problems/maximal-network-rank/)

### N^2 Solution

```csharp
public class Solution {
    public int MaximalNetworkRank(int n, int[][] roads) {
        HashSet<int>[] graph = new HashSet<int>[n];
        
        Node[] inDegrees = new Node[n];
        
        for(int i = 0; i < n; i++){
            graph[i] = new HashSet<int>();
            inDegrees[i] = new Node(i);
        }
        
        foreach(int[] road in roads){
            inDegrees[road[0]].degree++;
            inDegrees[road[1]].degree++;
            
            graph[road[0]].Add(road[1]);
            graph[road[1]].Add(road[0]);
        }
        
        int maxSoFar = 0;
        
        for(int i = 0; i < inDegrees.Length; i++){
            for(int j = i + 1; j < inDegrees.Length; j++){
                
                int currSum = inDegrees[i].degree + inDegrees[j].degree;
                
                if(this.AreConnected(graph, inDegrees[i], inDegrees[j])){
                    currSum -= 1;
                }
                
                maxSoFar = Math.Max(maxSoFar, currSum);
            }
        }
        
        return maxSoFar;
    }
    
    public bool AreConnected(HashSet<int>[] graph, Node a, Node b){
        if(graph[a.node].Contains(b.node)){
            return true;
        }
        
        return false;
    }
}

public class Node{
    public int node;
    public int degree;
    
    public Node(int node){
        this.node = node;
    }
}
```

### Space Optimized N^2 Solution

```csharp
public class Solution {
    public int MaximalNetworkRank(int n, int[][] roads) {
        HashSet<int>[] graph = new HashSet<int>[n];
        
        Node[] inDegrees = new Node[n];
        
        for(int i = 0; i < n; i++){
            graph[i] = new HashSet<int>();
            inDegrees[i] = new Node(i);
        }
        
        foreach(int[] road in roads){
            inDegrees[road[0]].degree++;
            inDegrees[road[1]].degree++;
            
            graph[road[0]].Add(road[1]);
            graph[road[1]].Add(road[0]);
        }
        
        Array.Sort(inDegrees, (a,b) => b.degree - a.degree);

        List<Node> tempList = new List<Node>();
        
        tempList.Add(inDegrees[0]);
        tempList.Add(inDegrees[1]);
        
        int tempDegree = inDegrees[1].degree;
        
        for(int i = 2; i < n; i++){
            if(tempDegree == inDegrees[i].degree){
                tempList.Add(inDegrees[i]);
            }
            else{
                break;
            }
        }
        
        int maxSoFar = 0;
        
        for(int i = 0; i < tempList.Count; i++){
            for(int j = i + 1; j < tempList.Count; j++){
                
                int currSum = tempList[i].degree + tempList[j].degree;
                
                if(this.AreConnected(graph, tempList[i], tempList[j])){
                    currSum -= 1;
                }

                maxSoFar = Math.Max(currSum, maxSoFar);
                
            }
        }
        
        return maxSoFar;
    }
    
    public bool AreConnected(HashSet<int>[] graph, Node a, Node b){
        if(graph[a.node].Contains(b.node)){
            return true;
        }
        
        return false;
    }
}

public class Node{
    public int node;
    public int degree;
    
    public Node(int node){
        this.node = node;
    }
}
```
