---
title: N-ary Tree Postorder Traversal
date: "2020-07-01"
type: problem-solving
description: N-ary Tree Postorder Traversal
tags: csharp
---

Note: This problem was taken from LeetCode - [N-ary Tree Postorder Traversal](https://leetcode.com/problems/n-ary-tree-postorder-traversal/)

### Using Recursion

```csharp
public IList<int> Postorder(Node root) {
	List<int> output = new List<int>();
	this.DFS(root, output);
	return output;
}

public void DFS(Node root, List<int> output){
	if(root == null){
		return;
	}
	
	foreach(Node node in root.children){
		this.DFS(node, output);    
	}
	
	output.Add(root.val);
}
```

### Using Iteration

```csharp
public IList<int> Postorder(Node root) {
	List<int> output = new List<int>();
	
	if(root == null){
		return output;
	}
	
	Stack<Node> st = new Stack<Node>();
	st.Push(root);
	
	while(st.Count > 0){
		Node tempNode = st.Pop();
		
		output.Add(tempNode.val);
		
		foreach(Node node in tempNode.children){
			st.Push(node);
		}
	}
	
	output.Reverse();
	return output;
}
```
