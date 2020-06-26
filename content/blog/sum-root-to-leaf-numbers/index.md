---
title: Sum Root to Leaf Numbers
date: "2020-06-26"
type: problem-solving
description: Sum Root to Leaf Numbers
tags: csharp
---

Note: This problem was taken from LeetCode - [Sum Root to Leaf Numbers](https://leetcode.com/problems/sum-root-to-leaf-numbers/)

### Using Depth First Search

```csharp
public int SumNumbers(TreeNode root) {
	int output = 0;
	this.DFS(root, 0, ref output);
	
	return output;
}

public void DFS(TreeNode root, int num, ref int sum){
	if(root == null){
		return;
	}
	
	int tempNum = (num * 10) + root.val;
	
	if(root.left == null && root.right == null){
		sum += tempNum;
		return;
	}
	
	this.DFS(root.left, tempNum, ref sum);
	this.DFS(root.right, tempNum, ref sum);
}
```
