---
title: Binary Tree Level Order Traversal
date: "2020-02-17"
type: problem-solving
description: Binary Tree Level Order Traversal
tags: csharp
---

Note: This problem was taken from LeetCode - [Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/)

### Breadth First Search

Simply performing a Breadth-First Search on the given root element will give you the required result.

```csharp
public IList<IList<int>> LevelOrder(TreeNode root) {
    IList<IList<int>> output = new List<IList<int>>();
    
    if(root == null){
        return output; 
    }
    
    Queue<TreeNode> bfsQueue = new Queue<TreeNode>();
    bfsQueue.Enqueue(root);
    
    while(bfsQueue.Count != 0){
        int levelSize = bfsQueue.Count;
        
        List<int> temp = new List<int>();
        
        for(int i = 0; i < levelSize; i++){
            TreeNode item = bfsQueue.Dequeue();
            temp.Add(item.val);
            
            if(item.left != null){
                bfsQueue.Enqueue(item.left);
            }
            
            if(item.right != null){
                bfsQueue.Enqueue(item.right);
            }
        }
        output.Add(temp);
    }
    return output;
}
```
