---
title: House Robber III
date: "2020-11-23"
type: problem-solving
description: House Robber III
tags: csharp
---

Note: This problem was taken from LeetCode - [House Robber III](https://leetcode.com/problems/house-robber-iii/)

### Using Recursion

```csharp
public int Rob(TreeNode root) {
	if(root == null){
		return 0;
	}
	
	int val = 0;
	
	if(root.left != null){
		val += this.Rob(root.left.left) + this.Rob(root.left.right);
	}
	
	if(root.right != null){
		val += this.Rob(root.right.left) + this.Rob(root.right.right);
	}
	
	return Math.Max(root.val + val, this.Rob(root.left) + this.Rob(root.right));
}
```

### Using Recursion + Memoization

```csharp
Dictionary<TreeNode, int> map = new Dictionary<TreeNode, int>();

public int Rob(TreeNode root) {
	if(root == null){
		return 0;
	}

	if(map.ContainsKey(root)){
		return map[root];
	}
	
	int val = 0;
	
	if(root.left != null){
		val += this.Rob(root.left.left) + this.Rob(root.left.right);
	}
	
	if(root.right != null){
		val += this.Rob(root.right.left) + this.Rob(root.right.right);
	}
	
	map[root] = Math.Max(root.val + val, this.Rob(root.left) + this.Rob(root.right));
	
	return map[root];
}
```

### Using Recursion - Space Optimised

```csharp
public int Rob(TreeNode root) {
	int[] output = this.Recurse(root);
	
	return Math.Max(output[0], output[1]);
}

public int[] Recurse(TreeNode root){
	if(root == null){
		return new int[2];
	}
	
	int[] left = this.Recurse(root.left);
	int[] right = this.Recurse(root.right);
	
	int[] output = new int[2];
	
	output[0] = Math.Max(left[0], left[1]) + Math.Max(right[0], right[1]);
	output[1] = root.val + left[0] + right[0];
	
	return output;
}
```
