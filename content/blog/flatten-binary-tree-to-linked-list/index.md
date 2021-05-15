---
title: Flatten Binary Tree to Linked List
date: "2021-05-15"
type: problem-solving
description: Flatten Binary Tree to Linked List
tags: csharp
---

Note: This problem was taken from LeetCode - [Flatten Binary Tree to Linked List](https://leetcode.com/problems/flatten-binary-tree-to-linked-list/)

### Using Recursion

```csharp
public void Flatten(TreeNode root) {
	if(root == null){
		return;
	}
	
	TreeNode rightNode = root.right;
	
	this.Flatten(root.left);
	
	root.right = root.left;
	root.left = null;
	
	while(root.right != null){
		root = root.right;
	}
	
	this.Flatten(rightNode);
	
	root.right = rightNode;
}
```
