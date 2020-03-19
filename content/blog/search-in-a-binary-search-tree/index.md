---
title: Search in a Binary Search Tree
date: "2020-03-19"
type: problem-solving
description: Search in a Binary Search Tree
tags: csharp
---

Note: This problem was taken from LeetCode - [Search in a Binary Search Tree](https://leetcode.com/problems/search-in-a-binary-search-tree/)

To solve this problem simply check if a given node value is equal to the `key`(value to be searched). If they match then return that node. If the node value is greater than the `key` then repeat the process by switching to right child of the tree. Else switch to the left child of the tree. 

This solution is similar to both the recursive and iterative approaches.

### Using Recursion

```csharp
public TreeNode SearchBST(TreeNode root, int val) {
    if(root == null){
        return null;
    }
    
    if(root.val == val){
        return root;
    }
    else if(root.val > val) {
        return this.SearchBST(root.left, val);
    }
    else{
        return this.SearchBST(root.right, val);
    }
}
```

### Using Iteration

```csharp
    public TreeNode SearchBST(TreeNode root, int val) {
        if(root == null){
            return null;
        }
        
        while(root != null){
            if(root.val == val){
                return root;
            }
            else if(root.val > val){
                root = root.left;
            }
            else{
                root = root.right;
            }
        }
        
        return null;
    }
```
