---
title: Range Sum of BST
date: "2020-04-16"
type: problem-solving
description: Range Sum of BST
tags: csharp
---

Note: This problem was taken from LeetCode - [Range Sum of BST](https://leetcode.com/problems/range-sum-of-bst/)

### Depth First Search

```csharp
public int RangeSumBST(TreeNode root, int L, int R) {
	if(root == null){
		return 0;
	}
	
	if(root.val >= L && root.val <= R){
		return root.val + this.RangeSumBST(root.left, L, R) + this.RangeSumBST(root.right, L, R);
	}
	else{
		return this.RangeSumBST(root.left, L, R) + this.RangeSumBST(root.right, L, R);
	}        
}
```
