---
title: Maximum Width of Binary Tree
date: "2020-07-09"
type: problem-solving
description: Maximum Width of Binary Tree
tags: csharp
---

Note: This problem was taken from LeetCode - [Maximum Width of Binary Tree](https://leetcode.com/problems/maximum-width-of-binary-tree/)

### Using Sorting & Binary Search

```csharp
public int WidthOfBinaryTree(TreeNode root) {
	return this.DFS(root, 0, 1, new List<int>(), new List<int>());
}

public int DFS(TreeNode root, int level, int order, List<int> left, List<int> right){
	if(root == null){
		return 0;
	}
	
	if(left.Count == level){
		left.Add(order);
		right.Add(order);
	}
	else{
		right[level] = order;
	}
	
	int curr = right[level] - left[level] + 1;
	int cLeft = this.DFS(root.left, level+1, 2*order, left, right);
	int cRight = this.DFS(root.right, level+1, 2*order+1, left, right);
	
	return Math.Max(curr, Math.Max(cLeft, cRight));
}
```
