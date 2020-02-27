---
title: Binary Tree Zigzag Level Order Traversal
date: "2020-02-27"
type: problem-solving
description: Binary Tree Zigzag Level Order Traversal
tags: csharp
---

Note: This problem was taken from LeetCode - [Binary Tree Zigzag Level Order Traversal](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/)

### Best Approach

This problem is exactly similar to [Binary Tree Level Order Traversal](/binary-tree-level-order-traversal/). The only difference here is that we print odd depth levels of the tree in the reverse order. In order to add this, simply maintain another variable called `depth` which is incremented on every level traversal. At the end of traversal of a level, check if the depth is odd. If it is odd then reverse the list of that level.

```csharp
public IList<IList<int>> ZigzagLevelOrder(TreeNode root) {
    IList<IList<int>> output = new List<IList<int>>();
    
    if(root == null){
        return output;
    }
    
    int depth = 0;
    Queue<TreeNode> bfsQueue = new Queue<TreeNode>();
    bfsQueue.Enqueue(root);
    
    while(bfsQueue.Count != 0){
        int count = bfsQueue.Count;
        List<int> temp = new List<int>();
        for(int i = 0; i < count; i++){
            TreeNode node = bfsQueue.Dequeue();
            
            if(node.left != null){
                bfsQueue.Enqueue(node.left);
            }
            
            if(node.right != null){
                bfsQueue.Enqueue(node.right);
            }
            
            temp.Add(node.val);
        }
        
        if(depth % 2 != 0){
            temp.Reverse();
        }
        
        depth++;
        output.Add(temp);
    }
    
    return output;
}
```
