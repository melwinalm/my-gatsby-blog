---
title: Even Odd Tree
date: "2020-10-04"
type: problem-solving
description: Even Odd Tree
tags: csharp
---

Note: This problem was taken from LeetCode - [Even Odd Tree](https://leetcode.com/problems/even-odd-tree/)

### Using Breadth First Search

```csharp
public bool IsEvenOddTree(TreeNode root) {
	if(root == null){
		return true;
	}

	Queue<TreeNode> bfsQueue = new Queue<TreeNode>();
	bfsQueue.Enqueue(root);

	int level = 1;
	
	while(bfsQueue.Count > 0){
		int count = bfsQueue.Count;
		
		int prevValue;
		
		if(level % 2 == 1){
			prevValue = 0;
		}
		else{
			prevValue = Int32.MaxValue;
		}
		
		for(int i = 0; i < count; i++){
			TreeNode tempNode = bfsQueue.Dequeue();
			
			if((level % 2 == 1 && tempNode.val % 2 == 1 && tempNode.val > prevValue) || (level % 2 == 0 && tempNode.val % 2 == 0 && tempNode.val < prevValue)){
				if(tempNode.left != null){
					bfsQueue.Enqueue(tempNode.left);
				}
				if(tempNode.right != null){
					bfsQueue.Enqueue(tempNode.right);
				}
				
				prevValue = tempNode.val;
			}
			else{
				return false;
			}
			
		}
		
		level++;
	}
	
	return true;
}
```
