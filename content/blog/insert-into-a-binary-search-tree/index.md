---
title: Insert into a Binary Search Tree
date: "2020-10-06"
type: problem-solving
description: Insert into a Binary Search Tree
tags: csharp
---

Note: This problem was taken from LeetCode - [Insert into a Binary Search Tree](https://leetcode.com/problems/insert-into-a-binary-search-tree/)

### Iterative Solution

```csharp
public TreeNode InsertIntoBST(TreeNode root, int val) {
	if(root == null){
		return new TreeNode(val);
	}
	
	TreeNode tempNode = root;
	TreeNode parentNode = null;        
	
	while(tempNode != null){
		parentNode = tempNode;
		
		if(tempNode.val < val){
			tempNode = tempNode.right;
		}
		else if(tempNode.val > val){
			tempNode = tempNode.left;
		}
	}
	
	if(val > parentNode.val){
		parentNode.right = new TreeNode(val);
	}
	else if(val < parentNode.val){
		parentNode.left = new TreeNode(val);
	}
	
	return root;
}
```

### Recursive Solution

```csharp
public TreeNode InsertIntoBST(TreeNode root, int val) {
	if(root == null){
		return new TreeNode(val);
	}
	
	if(val < root.val){
		root.left = this.InsertIntoBST(root.left, val);
	}
	else if(val > root.val){
		root.right = this.InsertIntoBST(root.right, val);
	}
	
	return root;
}
```
