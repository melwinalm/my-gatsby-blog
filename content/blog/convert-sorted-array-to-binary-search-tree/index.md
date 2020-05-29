---
title: Convert Sorted Array to Binary Search Tree
date: "2020-05-29"
type: problem-solving
description: Convert Sorted Array to Binary Search Tree
tags: csharp
---

Note: This problem was taken from LeetCode - [Convert Sorted Array to Binary Search Tree](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/)

### Using Depth First Search

```csharp
public TreeNode SortedArrayToBST(int[] nums) {
	if(nums.Length == 0){
		return null;
	}
	
	return this.DFS(nums, 0, nums.Length - 1);
}

public TreeNode DFS(int[] nums, int startIndex, int endIndex){
	if(startIndex > endIndex){
		return null;
	}
	
	int midIndex = startIndex + ((endIndex - startIndex)/2);
	
	TreeNode tempNode = new TreeNode(nums[midIndex]);
	tempNode.left = this.DFS(nums, startIndex, midIndex-1);
	tempNode.right = this.DFS(nums, midIndex+1, endIndex);
	
	return tempNode;
}  
```
