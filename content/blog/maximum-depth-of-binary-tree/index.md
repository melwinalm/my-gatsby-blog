---
title: Maximum Depth of Binary Tree
date: "2020-01-31"
type: problem-solving
description: Maximum Depth of Binary Tree
tags: csharp
---

Note: This problem was taken from LeetCode - [Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/)

### Breadth First Search

In breadth-first technique, a queue is maintained which stores all the nodes of a particular depth at one point. Iteratively loop through each depth levels of the binary tree. Keep doing this until the queue is empty(i.e. all the nodes of that depth do not have any child nodes).

```csharp
public int MaxDepth(TreeNode root) {
    if(root == null){
        return 0;
    }
    
    Queue<TreeNode> temp = new Queue<TreeNode>();
    temp.Enqueue(root);
    
    int depth = 0;
    
    while(temp.Count != 0){
        depth++;
        int size = temp.Count;
        for(int i = 0; i < size; i++){
            TreeNode node = temp.Dequeue();
            if(node.left != null){
                temp.Enqueue(node.left);
            }
            if(node.right != null){
                temp.Enqueue(node.right);
            }
        }
    }
    
    return depth;
}
```

### Depth First Search

Recursively call the `MaxDepth` method on the left and right nodes of a node. Keep adding the 1 during this process. This will return the maximum depth of the given binary tree.

```csharp
public int MaxDepth(TreeNode root) {
    if(root != null){
        return 1 + Math.Max(this.MaxDepth(root.left), this.MaxDepth(root.right));
    }
    else{
        return 0;
    }
}
```
