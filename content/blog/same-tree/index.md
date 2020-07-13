---
title: Same Tree
date: "2020-07-13"
type: problem-solving
description: Same Tree
tags: csharp
---

Note: This problem was taken from LeetCode - [Same Tree](https://leetcode.com/problems/same-tree/)

### Using Recursion

```csharp
public bool IsSameTree(TreeNode p, TreeNode q) {
	if(p == null && q == null){
		return true;
	}
	
	if(p == null || q == null){
		return false;
	}
	
	if(p.val != q.val){
		return false;
	}
	
	return this.IsSameTree(p.left, q.left) && this.IsSameTree(p.right, q.right);
}
```
