---
title: Average of Levels in Binary Tree
date: "2020-01-15"
type: problem-solving
description: Average of Levels in Binary Tree
tags: csharp
---

Note: This problem was taken from LeetCode - [Average of Levels in Binary Tree](https://leetcode.com/problems/average-of-levels-in-binary-tree/)

This problem can be solved using both Breadth First Search and Depth First Search. The most appropriate approach to solve this problem would be to use BFS, since we need an average of nodes at each level of depth, and BFS traverses at each depth level. 

See the following code which enqueues the root node first into the Queue, then enqueues the left and right nodes of the root node. Keep doing this recursively until all nodes are traversed. As and when the Queue is empty find their average and store it in a list. See the below code for the solution.

```csharp
public IList<double> AverageOfLevels(TreeNode root) {
    Queue<TreeNode> BFS = new Queue<TreeNode>();
    List<double> output = new List<double>();
    
    BFS.Enqueue(root);
    
    while(BFS.Count != 0){
        int levelSize = BFS.Count;
        double heightSum = 0;
        
        for(int i = 0; i < levelSize; i++){
            TreeNode currentNode = BFS.Dequeue();
            if(currentNode.left != null){
                BFS.Enqueue(currentNode.left);
            }
            if(currentNode.right != null){
                BFS.Enqueue(currentNode.right);
            }
            heightSum += currentNode.val;
        }
        output.Add(heightSum/levelSize);
    }
    return output.ToArray();
}
```
