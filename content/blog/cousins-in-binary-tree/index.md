---
title: Cousins in Binary Tree
date: "2020-05-07"
type: problem-solving
description: Cousins in Binary Tree
tags: csharp
---

Note: This problem was taken from LeetCode - [Cousins in Binary Tree](https://leetcode.com/problems/cousins-in-binary-tree/)

### Using Breadth First Search
```csharp
public bool IsCousins(TreeNode root, int x, int y) {
	Queue<TreeNode> bfsQueue = new Queue<TreeNode>();
	bfsQueue.Enqueue(root);
	
	while(bfsQueue.Count > 0){
		int count = bfsQueue.Count;
		
		bool xExists = false;
		bool yExists = false;
		
		for(int i = 0; i < count; i++){
			TreeNode temp = bfsQueue.Dequeue();
			
			if(temp.val == x){
				xExists = true;
			}
			if(temp.val == y){
				yExists = true;
			}
			
			if(temp.left != null && temp.right != null){
				if(temp.left.val == x && temp.right.val == y){
					return false;
				}
				if(temp.right.val == x && temp.left.val == y){
					return false;
				}
			}
			
			if(temp.left != null){
				bfsQueue.Enqueue(temp.left);
			}
			if(temp.right != null){
				bfsQueue.Enqueue(temp.right);
			}
		}
		
		if(xExists && yExists){
			return true;
		}
	}

	return false;
}
```
