---
title: Lowest Common Ancestor of a Binary Tree
date: "2020-06-06"
type: problem-solving
description: Lowest Common Ancestor of a Binary Tree
tags: csharp
---

Note: This problem was taken from LeetCode - [Lowest Common Ancestor of a Binary Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/)

### Using Depth First Search

```csharp
public TreeNode LowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
	List<TreeNode> path1 = new List<TreeNode>();
	List<TreeNode> path2 = new List<TreeNode>();
	
	this.FindNode(root, path1, p);
	this.FindNode(root, path2, q);
	
	int min = Math.Min(path1.Count, path2.Count);
	
	TreeNode output = null;
	
	for(int i = 0; i < min; i++){
		if(path1[i] == path2[i]){
			output = path1[i];
		}
		else{
			break;
		}
	}
	
	return output;
}

public bool FindNode(TreeNode root, List<TreeNode> path, TreeNode searchNode){
	if(root == null){
		return false;
	}        
	
	path.Add(root);
	
	if(root == searchNode){
		return true;
	}
	
	bool flag = this.FindNode(root.left, path, searchNode) || this.FindNode(root.right, path, searchNode);
	
	if(flag == true){
		return true;
	}
	else{
		// Backtrack
		path.RemoveAt(path.Count - 1);
		return false;
	}
}
```
