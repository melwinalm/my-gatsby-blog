---
title: Validate Binary Search Tree
date: "2020-02-12"
type: problem-solving
description: Validate Binary Search Tree
tags: csharp
---

Note: This problem was taken from LeetCode - [Validate Binary Search Tree](https://leetcode.com/problems/validate-binary-search-tree/)

### Using In-Order Traversal

Simply do an in-order traversal on tree starting from the root node and put node values in a list. Then check if the elements in the list are in ascending order. If yes then it is a valid Binary Search Tree.

```csharp
public bool IsValidBST(TreeNode root) {
    if(root == null){
        return true;
    }
    
    List<int> temp = new List<int>();
    
    this.InOrderTraversal(root, temp);
    
    for(int i = 1; i < temp.Count; i++){
        if(temp[i-1] >= temp[i]){
            return false;
        }
    }
    return true;
}

public void InOrderTraversal(TreeNode node, List<int> temp){
    if(node.left != null){
        this.InOrderTraversal(node.left, temp);
    }
    temp.Add(node.val);
    if(node.right != null){
        this.InOrderTraversal(node.right, temp);
    }
}
```

### Using Recursion

A min and max value integer is maintained for each node. Check if left and right nodes are in the low and high range. if any node violates the condition then it is not a valid BST. Call and check if the left and right nodes are invalid range recursively to get the required result.

```csharp
public bool IsValidBST(TreeNode root) {
      return this.ValidateBST(root, long.MinValue, long.MaxValue);
  }
  
  public bool ValidateBST(TreeNode node, long low, long high){
      if(node == null){
          return true;
      }
      
      if(low != null && node.val <= low){
          return false;
      }
      if(high != null && node.val >= high){
          return false;
      }
      
      if(!this.ValidateBST(node.left, low, node.val)){
          return false;
      }
      if(!this.ValidateBST(node.right, node.val, high)){
          return false;
      }
          
      return true;
  }
```

### Using Iteration

This problem can be solved using iterative method also. Maintain three different stacks (for node value, lower and upper values) and check if they meet the condtions by using Breadth-First Search technique.
