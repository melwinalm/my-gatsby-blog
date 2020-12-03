---
title: Increasing Order Search Tree
date: "2020-12-03"
type: problem-solving
description: Increasing Order Search Tree
tags: csharp
---

Note: This problem was taken from LeetCode - [Increasing Order Search Tree](https://leetcode.com/problems/increasing-order-search-tree/)

### Using Recursion

```csharp
TreeNode head;
public TreeNode IncreasingBST(TreeNode root) {
	TreeNode output = new TreeNode(0);
	head = output;
	this.InOrder(root);
	return output.right;
}

public void InOrder(TreeNode root){
	if(root == null){
		return;
	}
	
	this.InOrder(root.left);
	
	root.left = null;
	head.right = root;
	head = root;
	
	this.InOrder(root.right);
}
```
