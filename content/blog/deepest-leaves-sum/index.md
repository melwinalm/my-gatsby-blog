---
title: Deepest Leaves Sum
date: "2020-03-17"
type: problem-solving
description: Deepest Leaves Sum
tags: csharp
---

Note: This problem was taken from LeetCode - [Deepest Leaves Sum](https://leetcode.com/problems/deepest-leaves-sum/)

### Level Order Traversal

Perform a level order traversal on the given root node. As each level of the tree is traversed, add the node values and store it in a variable. Clear the sum when traversing through the next level. Keep repeating it until the last level to get the required result. 

```csharp
public int DeepestLeavesSum(TreeNode root) {
    Queue<TreeNode> bfsQueue = new Queue<TreeNode>();
    
    if(root == null){
        return 0;
    }
    
    bfsQueue.Enqueue(root);
    
    int output = 0;
    
    while(bfsQueue.Count != 0){
        int count = bfsQueue.Count;
        output = 0;
        for(int i = 0; i < count; i++){
            TreeNode temp = bfsQueue.Dequeue();
            output += temp.val;
            
            if(temp.left != null){
                bfsQueue.Enqueue(temp.left);
            }
            
            if(temp.right != null){
                bfsQueue.Enqueue(temp.right);
            }
        }
    }
    
    return output;
}
```
