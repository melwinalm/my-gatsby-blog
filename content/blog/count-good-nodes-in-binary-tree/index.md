---
title: Count Good Nodes in Binary Tree
date: "2020-05-16"
type: problem-solving
description: Count Good Nodes in Binary Tree
tags: csharp
---

Note: This problem was taken from LeetCode - [Count Good Nodes in Binary Tree](https://leetcode.com/problems/count-good-nodes-in-binary-tree/)

### Using DFS

```csharp
public int GoodNodes(TreeNode root) {
	int count = 0;
	this.GoodNodes(root, Int32.MinValue, ref count);
	
	return count;
}

public void GoodNodes(TreeNode root, int maxValue, ref int count){
	if(root == null){
		return;
	}
	
	if(root.val >= maxValue){
		count++;
	}
	
	this.GoodNodes(root.left, Math.Max(root.val, maxValue), ref count);
	this.GoodNodes(root.right, Math.Max(root.val, maxValue), ref count);
}
```
