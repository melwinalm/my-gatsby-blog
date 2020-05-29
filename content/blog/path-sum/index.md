---
title: Path Sum
date: "2020-05-29"
type: problem-solving
description: Path Sum
tags: csharp
---

Note: This problem was taken from LeetCode - [Path Sum](https://leetcode.com/problems/path-sum/)

### Using Depth First Search

```csharp
public bool HasPathSum(TreeNode root, int sum) {
	if(root == null){
		return false;
	}
	
	sum -= root.val;
	
	if(root.left == null && root.right == null){
		return sum == 0 ? true : false;
	}
	
	return this.HasPathSum(root.left, sum) || this.HasPathSum(root.right, sum);
}  
```
