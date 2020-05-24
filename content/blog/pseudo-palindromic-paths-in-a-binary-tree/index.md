---
title: Pseudo-Palindromic Paths in a Binary Tree
date: "2020-05-24"
type: problem-solving
description: Pseudo-Palindromic Paths in a Binary Tree
tags: csharp
---

Note: This problem was taken from LeetCode - [Pseudo-Palindromic Paths in a Binary Tree](https://leetcode.com/problems/pseudo-palindromic-paths-in-a-binary-tree/)

### Using Depth First Search

```csharp
public int PseudoPalindromicPaths (TreeNode root) {
	int count = 0;
	int[] nodeValues = new int[9];
	
	this.DFS(root, nodeValues, ref count);        
	return count;
}

public void DFS(TreeNode root, int[] nodeValues, ref int count){
	if(root == null){
		return;
	}
	
	nodeValues[root.val - 1]++;
	
	if(root.left == null && root.right == null){
		if(this.IsPseudoPalindromic(nodeValues)){
			count++;
		}
	}
	
	this.DFS(root.left, nodeValues, ref count);
	this.DFS(root.right, nodeValues, ref count);
	
	nodeValues[root.val - 1]--; // Backtracking to previous value
}

public bool IsPseudoPalindromic(int[] nodeValues){
	bool flag = true;
	
	for(int i = 0; i < nodeValues.Length; i++){
		if(nodeValues[i] == 0){
			continue;
		}
		
		if(nodeValues[i] % 2 != 0){
			if(flag == true){
				flag = false;
			}
			else{
				return false;
			}
		}
	}
	
	return true;
}
```
