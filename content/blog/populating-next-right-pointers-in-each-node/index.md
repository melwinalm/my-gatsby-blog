---
title: Populating Next Right Pointers in Each Node
date: "2020-11-14"
type: problem-solving
description: Populating Next Right Pointers in Each Node
tags: csharp
---

Note: This problem was taken from LeetCode - [Populating Next Right Pointers in Each Node](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/)

### Using Breadth First Search

```csharp
public Node Connect(Node root) {
	if(root == null){
		return root;
	}
	
	Queue<Node> bfs = new Queue<Node>();
	bfs.Enqueue(root);
	
	while(bfs.Count > 0){
		int count = bfs.Count;
		
		for(int i = 0; i < count; i++){
			Node tempNode = bfs.Dequeue();
			
			if(i != count - 1){
				tempNode.next = bfs.Peek();
			}
			
			if(tempNode.left != null){
				bfs.Enqueue(tempNode.left);
			}
			
			if(tempNode.right != null){
				bfs.Enqueue(tempNode.right);
			}
		}
	}
	
	return root;
}
```

### Better Solution (Constant space)

```csharp
public Node Connect(Node root) {
	if(root == null){
		return root;
	}
	
	Node prev = root;
	Node curr = null;
	
	while(prev.left != null){
		curr = prev;
		
		while(curr != null){
			curr.left.next = curr.right;
			if(curr.next != null){
				curr.right.next = curr.next.left;
			}
			curr = curr.next;
		}
		prev = prev.left;
	}
	
	return root;
}
```
