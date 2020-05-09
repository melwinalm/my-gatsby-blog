---
title: Sum of Left Leaves
date: "2020-05-09"
type: problem-solving
description: Sum of Left Leaves
tags: csharp
---

Note: This problem was taken from LeetCode - [Sum of Left Leaves](https://leetcode.com/problems/sum-of-left-leaves/)

### Using Recursion

```csharp
public int SumOfLeftLeaves(TreeNode root) {
	int count = 0;
	return this.SumOfLeftLeaves(root, false);
}

public int SumOfLeftLeaves(TreeNode root, bool isLeft){
	if(root == null){
		return 0;
	}
	
	if(root.left == null && root.right == null){
		if(isLeft){
			return root.val;
		}
		else{
			return 0;
		}
	}
	
	return this.SumOfLeftLeaves(root.left, true) + this.SumOfLeftLeaves(root.right, false);
}
```
