---
title: Minimum Depth of Binary Tree
date: "2020-05-29"
type: problem-solving
description: Minimum Depth of Binary Tree
tags: csharp
---

Note: This problem was taken from LeetCode - [Minimum Depth of Binary Tree](https://leetcode.com/problems/minimum-depth-of-binary-tree/)

### Using Breadth First Search

```csharp
public int MinDepth(TreeNode root) {
	if(root == null){
		return 0;
	}
	
	Queue<TreeNode> bfsQueue = new Queue<TreeNode>();
	bfsQueue.Enqueue(root);
	
	int depthCount = 0;
	
	while(bfsQueue.Count > 0){
		int count = bfsQueue.Count;
		depthCount++;
		
		for(int i = 0; i < count; i++){
			TreeNode tempNode = bfsQueue.Dequeue();
			
			if(tempNode.left == null && tempNode.right == null){
				return depthCount;
			}
			
			if(tempNode.left != null){
				bfsQueue.Enqueue(tempNode.left);   
			}
			
			if(tempNode.right != null){
				bfsQueue.Enqueue(tempNode.right);   
			}
		}
	}

	return depthCount;
}
```

### Using Depth First Search

```csharp
public int MinDepth(TreeNode root) {
	if(root == null){
		return 0;
	}
	
	int left = this.MinDepth(root.left);
	int right = this.MinDepth(root.right);
	
	if(left == 0){
		return 1 + right;
	}
	else if (right == 0){
		return 1 + left;
	}
	else{
		return 1 + Math.Min(left, right);
	}
}
```
