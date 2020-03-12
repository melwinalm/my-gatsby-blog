---
title: Check Completeness of a Binary Tree
date: "2020-03-12"
type: problem-solving
description: Check Completeness of a Binary Tree
tags: csharp
---

Note: This problem was taken from LeetCode - [Check Completeness of a Binary Tree](https://leetcode.com/problems/check-completeness-of-a-binary-tree/)

### Level Order Traversal

Perform a Level Order Traversal on the given binary tree. Break the loop when you find an empty node. All the nodes after that should be empty. If you find a non-empty node then it is not a complete binary tree.

```csharp
public bool IsCompleteTree(TreeNode root) {
    if(root == null){
        return true;
    }
    
    Queue<TreeNode> bfsQueue = new Queue<TreeNode>();
    bfsQueue.Enqueue(root);
    
    while(bfsQueue.Count != 0){
        TreeNode tempNode = bfsQueue.Dequeue();
        
        if(tempNode == null){
            break;
        }
        bfsQueue.Enqueue(tempNode.left);
        bfsQueue.Enqueue(tempNode.right);
    }
    
    while(bfsQueue.Count != 0){
        TreeNode tempNode = bfsQueue.Dequeue();
        if(tempNode != null){
            return false;
        }
    }    
    
    return true;
}
```
