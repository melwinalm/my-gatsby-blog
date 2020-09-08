---
title: Sum of Root To Leaf Binary Numbers
date: "2020-09-08"
type: problem-solving
description: Sum of Root To Leaf Binary Numbers
tags: csharp
---

Note: This problem was taken from LeetCode - [Sum of Root To Leaf Binary Numbers](https://leetcode.com/problems/sum-of-root-to-leaf-binary-numbers/)

### Using Recursion

```csharp
public int SumRootToLeaf(TreeNode root) {
	return this.Sum(root, 0);
}

public int Sum(TreeNode node, int valueSoFar){
	if(node == null){
		return 0;
	}
	
	valueSoFar = valueSoFar * 2 + node.val;
	
	if(node.left == null && node.right == null){
		return valueSoFar;
	}
	else{
		return this.Sum(node.left, valueSoFar) + this.Sum(node.right, valueSoFar);
	}
}
```
