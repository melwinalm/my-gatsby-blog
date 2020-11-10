---
title: Maximum Difference Between Node and Ancestor
date: "2020-11-10"
type: problem-solving
description: Maximum Difference Between Node and Ancestor
tags: csharp
---

Note: This problem was taken from LeetCode - [Maximum Difference Between Node and Ancestor](https://leetcode.com/problems/maximum-difference-between-node-and-ancestor/)

### Using Recursion

```csharp
public class Solution {
    
    int maxSoFar = 0;
    public int MaxAncestorDiff(TreeNode root) {
        if(root == null){
            return 0;
        }
        
        this.Recurse(root, root.val, root.val);
        
        return maxSoFar;
    }
    
    public void Recurse(TreeNode root, int min, int max){
        if(root == null){
            return;
        }

        maxSoFar = Math.Max(maxSoFar, Math.Max(Math.Abs(root.val - min), Math.Abs(root.val - max)));
        
        int currMin = Math.Min(min, root.val);
        int currMax = Math.Max(max, root.val);
        
        this.Recurse(root.left, currMin, currMax);
        this.Recurse(root.right, currMin, currMax);
    }
}
```
