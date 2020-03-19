---
title: Maximum Depth of N-ary Tree
date: "2020-03-19"
type: problem-solving
description: Maximum Depth of N-ary Tree
tags: csharp
---

Note: This problem was taken from LeetCode - [Maximum Depth of N-ary Tree](https://leetcode.com/problems/maximum-depth-of-n-ary-tree/)

### BFS Approach

Perform a breadth-first search on the given root node. Maintain a variable `depth` to keep track of the number of levels that are traversed.

```csharp
public int MaxDepth(Node root) {
    if(root == null){
        return 0;
    }
    
    Queue<Node> bfsQueue = new Queue<Node>();
    bfsQueue.Enqueue(root);
    int depth = 0;
    
    while(bfsQueue.Count != 0){
        int count = bfsQueue.Count;
        depth++;
        
        for(int i = 0; i < count; i++){
            Node tempNode = bfsQueue.Dequeue();
            foreach(Node temp in tempNode.children){
                bfsQueue.Enqueue(temp);
            }
        }
    }
    
    return depth;  
}
```

### DFS Search

```csharp
public int MaxDepth(Node root) {
    if (root == null){
        return 0;
    }
    int depth = 0;
    foreach(Node temp in root.children){
        depth = Math.Max(depth, this.MaxDepth(temp));
    }
    return 1 + depth;
}
```
