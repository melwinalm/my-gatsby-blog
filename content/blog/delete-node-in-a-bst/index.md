---
title: Delete Node in a BST
date: "2020-08-31"
type: problem-solving
description: Delete Node in a BST
tags: csharp
---

Note: This problem was taken from LeetCode - [Delete Node in a BST](https://leetcode.com/problems/delete-node-in-a-bst/)

### Using Recursion

There are 3 scenarios for deleting a case:

If the node to be deleted is:

- Leaf Node - Delete that node.
- Only one child - Replace the node to be deleted with its child node
- Two children - Find the successor(of the node to be deleted by traversing all the way to the left most node of the that tree in the right subtree of the node to be deleted).

```csharp
public TreeNode DeleteNode(TreeNode root, int key) {
	if(root == null){
		return root;
	}
	
	if(root.val > key){
		root.left = this.DeleteNode(root.left, key);
	}
	else if(root.val < key){
		root.right = this.DeleteNode(root.right, key);
	}
	else{
		if(root.left == null && root.right == null){
			return null;
		}
		else if(root.left == null){
			return root.right;
		}
		else if(root.right == null){
			return root.left;
		}
		else{
			TreeNode succ = this.GetSuccessor(root);
			root.val = succ.val;
			root.right = this.DeleteNode(root.right, succ.val);
		}
	}
	
	return root;
}

public TreeNode GetSuccessor(TreeNode root){
	TreeNode curr = root.right;
	
	while(curr != null && curr.left != null){
		curr = curr.left;
	}
	
	return curr;
}
```
