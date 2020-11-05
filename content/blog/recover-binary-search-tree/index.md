---
title: Recover Binary Search Tree
date: "2020-11-05"
type: problem-solving
description: Recover Binary Search Tree
tags: csharp
---

Note: This problem was taken from LeetCode - [Recover Binary Search Tree](https://leetcode.com/problems/recover-binary-search-tree/)

### Using InOrder Traversal

```csharp
public void RecoverTree(TreeNode root) {
	
	TreeNode prevNode = null;
	TreeNode firstNode = null;
	TreeNode secondNode = null;
	
	this.InOrder(root, ref prevNode, ref firstNode, ref secondNode);
	
	int temp = firstNode.val;
	firstNode.val = secondNode.val;
	secondNode.val = temp;
	
}

public void InOrder(TreeNode currNode, ref TreeNode prevNode, ref TreeNode firstNode, ref TreeNode secondNode){
	if(currNode == null){
		return;
	}
	
	this.InOrder(currNode.left, ref prevNode, ref firstNode, ref secondNode);
	
	if(prevNode != null){
		if(prevNode.val > currNode.val){
			if(firstNode == null){
				firstNode = prevNode;
			}
			secondNode = currNode;
		}
	}
	
	prevNode = currNode;
	
	this.InOrder(currNode.right, ref prevNode, ref firstNode, ref secondNode);
}
```
