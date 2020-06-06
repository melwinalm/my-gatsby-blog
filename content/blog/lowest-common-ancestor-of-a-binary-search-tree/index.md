---
title: Lowest Common Ancestor of a Binary Search Tree
date: "2020-06-06"
type: problem-solving
description: Lowest Common Ancestor of a Binary Search Tree
tags: csharp
---

Note: This problem was taken from LeetCode - [Lowest Common Ancestor of a Binary Search Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/)

### Using Level Order Traversal

Iteratively check if both search nodes belong to the same child (left or right child) of a node. If they belong to the same child nodes, then repeat this to the next level of the tree. If the search nodes belong to different child nodes then that is the ancestor node.

```csharp
public TreeNode LowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
	TreeNode output = root;
	
	while(root != null){
		if(p.val < root.val && q.val < root.val){
			root = root.left;
		}
		else if(p.val > root.val && q.val > root.val){
			root = root.right;
		}
		else{
			output = root;
			break;
		}
	}
	
	return root;
}
```
