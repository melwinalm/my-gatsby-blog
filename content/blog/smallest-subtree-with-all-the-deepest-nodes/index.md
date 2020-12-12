---
title: Smallest Subtree with all the Deepest Nodes
date: "2020-12-12"
type: problem-solving
description: Smallest Subtree with all the Deepest Nodes
---

Note: This problem was taken from LeetCode - [Smallest Subtree with all the Deepest Nodes](https://leetcode.com/problems/smallest-subtree-with-all-the-deepest-nodes/)

### Recursion

```csharp
public class Solution {
    public TreeNode SubtreeWithAllDeepest(TreeNode root) {
        if(root == null){
            return null;
        }
        
        return this.FindDepth(root, 0).key;
    }
    
    private Pair FindDepth(TreeNode root, int depth){
        if(root == null){
            return new Pair(null, depth);
        }
        
        Pair left = this.FindDepth(root.left, depth+1);
        Pair right = this.FindDepth(root.right, depth+1);
        
        if(left.value > right.value){
            return left;
        }
        else if(left.value < right.value){
            return right;
        }
        else{
            return new Pair(root, left.value);
        }
    }
}

public class Pair{
    public TreeNode key;
    public int value;
    
    public Pair(TreeNode key, int value){
        this.key = key;
        this.value = value;
    }
}
```
