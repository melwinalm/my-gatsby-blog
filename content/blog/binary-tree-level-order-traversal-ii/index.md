---
title: Binary Tree Level Order Traversal II
date: "2020-07-01"
type: problem-solving
description: Binary Tree Level Order Traversal II
tags: csharp
---

Note: This problem was taken from LeetCode - [Binary Tree Level Order Traversal II](https://leetcode.com/problems/binary-tree-level-order-traversal-ii/)

### Using Level Order Traversal

```csharp
public IList<IList<int>> LevelOrderBottom(TreeNode root) {
	IList<IList<int>> output = new List<IList<int>>();
	
	if(root == null){
		return output;
	}
	
	Queue<TreeNode> bfsQueue = new Queue<TreeNode>();
	bfsQueue.Enqueue(root);
	
	while(bfsQueue.Count > 0){
		int count = bfsQueue.Count;
		
		List<int> tempList = new List<int>();
		for(int i = 0; i < count; i++){
			TreeNode tempNode = bfsQueue.Dequeue();
			
			tempList.Add(tempNode.val);
			
			if(tempNode.left != null){
				bfsQueue.Enqueue(tempNode.left);
			}
			
			if(tempNode.right != null){
				bfsQueue.Enqueue(tempNode.right);
			}
			
		}
		output.Insert(0,tempList);
	}
	
	return output;
}
```
