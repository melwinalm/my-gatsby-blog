---
title: Clone Graph
date: "2020-06-01"
type: problem-solving
description: Clone Graph
tags: csharp
---

Note: This problem was taken from LeetCode - [Clone Graph](https://leetcode.com/problems/clone-graph/)

### Using Depth First Search

```csharp
public Node CloneGraph(Node node) {
	Dictionary<Node, Node> map = new Dictionary<Node, Node>();
	
	return this.Clone(node, map);
}

public Node Clone(Node node, Dictionary<Node, Node> map){
	if (node == null){
		return null;
	}

	if(map.ContainsKey(node)){
		return map[node];
	}
	
	Node tempNode = new Node(node.val);
	map[node] = tempNode;
	
	List<Node> vertices = new List<Node>();
	foreach(Node item in node.neighbors){
		vertices.Add(this.Clone(item, map));            
	}
	tempNode.neighbors = vertices;
	
	return tempNode;
}
```
