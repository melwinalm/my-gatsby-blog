---
title: Binary Tree Right Side View
date: "2020-04-01"
type: problem-solving
description: Binary Tree Right Side View
tags: csharp
---

Note: This problem was taken from LeetCode - [Binary Tree Right Side View](https://leetcode.com/problems/binary-tree-right-side-view/)

### Breadth-First Search Approach

```csharp
public IList<int> RightSideView(TreeNode root) {
    List<int> output = new List<int>();
    
    if(root == null){
        return output;
    }
    
    Queue<TreeNode> bfsQueue = new Queue<TreeNode>();
    bfsQueue.Enqueue(root);
    
    while(bfsQueue.Count > 0){
        int count = bfsQueue.Count;
        
        int last = 0;
        
        for(int i = 0; i < count; i++){
            TreeNode tempNode = bfsQueue.Dequeue();
            
            last = tempNode.val;
            
            if(tempNode.left != null){
                bfsQueue.Enqueue(tempNode.left);
            }
            
            if(tempNode.right != null){
                bfsQueue.Enqueue(tempNode.right);
            }
        }
        
        output.Add(last);
    }
    
    return output.ToArray();
}
```
