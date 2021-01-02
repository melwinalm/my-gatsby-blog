---
title: Find a Corresponding Node of a Binary Tree in a Clone of That Tree
date: "2021-01-02"
type: problem-solving
description: Find a Corresponding Node of a Binary Tree in a Clone of That Tree
---

Note: This problem was taken from LeetCode - [Find a Corresponding Node of a Binary Tree in a Clone of That Tree](https://leetcode.com/problems/find-a-corresponding-node-of-a-binary-tree-in-a-clone-of-that-tree/)

### Breadth First Search Approach

```csharp
public TreeNode GetTargetCopy(TreeNode original, TreeNode cloned, TreeNode target) {
	
	Queue<Tuple<TreeNode, TreeNode>> bfsQueue = new Queue<Tuple<TreeNode, TreeNode>>();
	bfsQueue.Enqueue(new Tuple<TreeNode, TreeNode>(original, cloned));
	
	while(bfsQueue.Count > 0){
		int count = bfsQueue.Count;
		
		for(int i = 0; i < count; i++){
			Tuple<TreeNode, TreeNode> temp = bfsQueue.Dequeue();
			
			if(temp.Item1 == target){
				return temp.Item2;
			}
			
			if(temp.Item1.left != null){
				bfsQueue.Enqueue(new Tuple<TreeNode, TreeNode>(temp.Item1.left, temp.Item2.left));
			}
			
			if(temp.Item1.right != null){
				bfsQueue.Enqueue(new Tuple<TreeNode, TreeNode>(temp.Item1.right, temp.Item2.right));
			}
		}
	}
	
	return null;
}
```
