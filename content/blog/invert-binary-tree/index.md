---
title: Invert Binary Tree
date: "2020-06-01"
type: problem-solving
description: Invert Binary Tree
tags: csharp
---

Note: This problem was taken from LeetCode - [Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree/)

### Using Depth First Search

```csharp
public TreeNode InvertTree(TreeNode root) {
	if(root == null){
		return root;
	}
	
	TreeNode left = this.InvertTree(root.left);
	TreeNode right = this.InvertTree(root.right);
	
	root.right = left;
	root.left = right;
	
	return root;
}
```

### Using Breadth First Search

```csharp
public TreeNode InvertTree(TreeNode root) {
	if(root == null){
		return root;
	}
	
	Queue<TreeNode> bfsQueue = new Queue<TreeNode>();
	bfsQueue.Enqueue(root);
	
	while(bfsQueue.Count > 0){
		TreeNode temp = bfsQueue.Dequeue();
		
		TreeNode tempLeft = temp.left;
		TreeNode tempRight = temp.right;
		
		temp.left = tempRight;
		temp.right = tempLeft;
		
		if(temp.left != null){
			bfsQueue.Enqueue(temp.left);
		}
		
		if(temp.right != null){
			bfsQueue.Enqueue(temp.right);
		}
	}
	
	return root;
}
```
