---
title: Count Complete Tree Nodes
date: "2020-06-23"
type: problem-solving
description: Count Complete Tree Nodes
tags: csharp
---

Note: This problem was taken from LeetCode - [Count Complete Tree Nodes](https://leetcode.com/problems/count-complete-tree-nodes/)

### Using Breadth First Search Approach

```csharp
public int CountNodes(TreeNode root) {
	if(root == null){
		return 0;
	}
	
	Queue<TreeNode> bfsQueue = new Queue<TreeNode>();
	bfsQueue.Enqueue(root);
	int nodeCount = 0;
	
	while(bfsQueue.Count > 0){
		int count = bfsQueue.Count;
		nodeCount += count;
		
		for(int i = 0; i < count; i++){
			TreeNode tempNode = bfsQueue.Dequeue();
			
			if(tempNode.left != null){
				bfsQueue.Enqueue(tempNode.left);
			}
			
			if(tempNode.right != null){
				bfsQueue.Enqueue(tempNode.right);
			}
		}
		
	}
	
	return nodeCount;
}
```
