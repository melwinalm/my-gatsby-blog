---
title: Binary Tree Paths
date: "2020-06-02"
type: problem-solving
description: Binary Tree Paths
tags: csharp
---

Note: This problem was taken from LeetCode - [Binary Tree Paths](https://leetcode.com/problems/binary-tree-paths/)

### Updating next pointer

```csharp
public IList<string> BinaryTreePaths(TreeNode root) {
	List<string> output = new List<string>();
	
	if(root == null){
		return output;
	}
	
	this.Paths(root, output, "");
	return output;
}

public void Paths(TreeNode root, List<string> output, string path){
	if(root.left == null && root.right == null){
		output.Add(path + root.val);
		return;
	}
			
	if(root.left != null){
		this.Paths(root.left, output, path + root.val + "->");
	}
	
	if(root.right != null){
		this.Paths(root.right, output, path + root.val + "->");
	}
}
```
