---
title: Binary Search Tree Iterator
date: "2020-12-10"
type: problem-solving
description: Binary Search Tree Iterator
tags: csharp
---

Note: This problem was taken from LeetCode - [Binary Search Tree Iterator](https://leetcode.com/problems/binary-search-tree-iterator/)

### Naive Approach

```csharp
List<int> nums;
int index;

public BSTIterator(TreeNode root) {
	index = 0;
	nums = new List<int>();
	this.InOrder(root);
}

private void InOrder(TreeNode root){
	if(root == null){
		return;
	}
	
	this.InOrder(root.left);
	this.nums.Add(root.val);
	this.InOrder(root.right);
}

public int Next() {
	index++;
	return nums[index-1];
}

public bool HasNext() {
	return index < nums.Count ? true : false;
}
```

### Using Stack

```csharp
Stack<TreeNode> st;

public BSTIterator(TreeNode root) {
	st = new Stack<TreeNode>();
	
	this.LeftMostInOrder(root);
}

private void LeftMostInOrder(TreeNode root){
	while(root != null){
		this.st.Push(root);
		root = root.left;
	}
}

public int Next() {
	TreeNode temp = this.st.Pop();
	
	if(temp.right != null){
		this.LeftMostInOrder(temp.right);
	}
	
	return temp.val;
}

public bool HasNext() {
	return st.Count > 0 ? true : false;
}
```
