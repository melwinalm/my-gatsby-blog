---
title: Balanced Binary Tree
date: "2020-12-23"
type: problem-solving
description: Balanced Binary Tree
---

Note: This problem was taken from LeetCode - [Balanced Binary Tree](https://leetcode.com/problems/balanced-binary-tree/)

### Recursion

```csharp
bool output = true;
public bool IsBalanced(TreeNode root) {
	this.MaxDepth(root);
	return output;
}

public int MaxDepth(TreeNode root){
	if(root == null){
		return 0;
	}
	
	int left = this.MaxDepth(root.left);
	int right = this.MaxDepth(root.right);
	
	if(Math.Abs(left - right) > 1){
		output = false;
	}
	
	return 1 + Math.Max(left, right);
}
```
