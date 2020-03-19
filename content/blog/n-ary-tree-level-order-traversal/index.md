---
title: N-ary Tree Level Order Traversal
date: "2020-03-19"
type: problem-solving
description: N-ary Tree Level Order Traversal
tags: csharp
---

Note: This problem was taken from LeetCode - [N-ary Tree Level Order Traversal](https://leetcode.com/problems/n-ary-tree-level-order-traversal/)


### Breadth-First Search Approach

The solution to this problem is a typical BFS approach, where you enqueue all the nodes of a level to a `Queue`. And when dequeuing the nodes, you enqueue the children of those to the `Queue`. Keep repeating this process until the `Queue` goes empty.

```csharp
public IList<IList<int>> LevelOrder(Node root) {
    IList<IList<int>> output = new List<IList<int>>();
    
    if(root == null){
        return output;
    }
    
    Queue<Node> bfsQueue = new Queue<Node>();
    bfsQueue.Enqueue(root);
    
    while(bfsQueue.Count != 0){
        int count = bfsQueue.Count;

        List<int> temp = new List<int>();
        
        for(int i = 0; i < count; i++){
            Node tempNode = bfsQueue.Dequeue();
            
            temp.Add(tempNode.val);
            foreach(Node item in tempNode.children){
                bfsQueue.Enqueue(item);
            }
        }
        output.Add(temp);
    }
    
    return output;
}
```
