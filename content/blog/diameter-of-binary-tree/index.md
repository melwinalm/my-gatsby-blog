---
title: Diameter of Binary Tree
date: "2020-04-11"
type: problem-solving
description: Diameter of Binary Tree
tags: csharp
---

Note: This problem was taken from LeetCode - [Diameter of Binary Tree](https://leetcode.com/problems/diameter-of-binary-tree/)

### Depth First Search

```csharp
public class Solution {
    int diameter = 0;
    public int DiameterOfBinaryTree(TreeNode root) {
        this.Depth(root);
        
        return diameter;
    }
    
    public int Depth(TreeNode node){
        if(node == null){
            return 0;
        }
        
        int lDepth = this.Depth(node.left);
        int rDepth = this.Depth(node.right);
        
        diameter = Math.Max(diameter, lDepth + rDepth);
        
        return Math.Max(lDepth, rDepth) + 1;
    }
}
```
