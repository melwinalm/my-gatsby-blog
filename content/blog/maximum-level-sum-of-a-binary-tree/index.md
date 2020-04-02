---
title: Maximum Level Sum of a Binary Tree
date: "2020-04-02"
type: problem-solving
description: Maximum Level Sum of a Binary Tree
tags: csharp
---

Note: This problem was taken from LeetCode - [Maximum Level Sum of a Binary Tree](https://leetcode.com/problems/maximum-level-sum-of-a-binary-tree/)

### Breadth First Search

```csharp
public int MaxLevelSum(TreeNode root) {
    if(root == null){
        return 0;
    }
    
    Queue<TreeNode> bfsQueue = new Queue<TreeNode>();
    bfsQueue.Enqueue(root);
    
    int max = Int32.MinValue;
    int minLevel = 0;
    int depth = 0;
    
    while(bfsQueue.Count > 0){
        int count = bfsQueue.Count;
        int sum = 0;
        depth++;
        
        for(int i = 0; i < count; i++){
            TreeNode tempNode = bfsQueue.Dequeue();
            
            sum += tempNode.val;
            
            if(tempNode.left != null){
                bfsQueue.Enqueue(tempNode.left);
            }
            
            if(tempNode.right != null){
                bfsQueue.Enqueue(tempNode.right);
            }
        }
        
        if(sum > max){
            max = sum;
            minLevel = depth;
        }
    }
    
    return minLevel;
}
```
