---
title: Implement Union Find (Disjoint Set) Data Structure
date: "2020-08-30"
type: problem-solving
description: Implement Union Find (Disjoint Set) Data Structure
tags: csharp
---

### Implementation of Union Find Data Structure

```csharp
public class UnionFind{
	
	int count; // Holds the number of connected components in the graph
	int[] size;
	int[] id;
	
	public UnionFind(int N){
		this.count = N;
		
		size = new int[N];
		id = new int[N];
		
		// Initially the size of all the nodes will be 1
		for(int i = 0; i < N; i++){
			size[i] = 1;
			id[i] = i;
		}
	}
	
	public int Find(int node){
		int root = node;
		
		// Loop until you find the parent of a node to be same as parent node
		while(root != id[root]){
			root = id[root];
		}
		
		// Applying path compression for better time complexity
		while(node != root){
			int newNode = id[node];
			id[node] = root;
			node = newNode;
		}
		
		return root;
	}
	
	public void Unify(int a, int b){
		int aParent = this.Find(a);
		int bParent = this.Find(b);
		
		if(aParent == bParent){
			return;
		}
		
		if(size[aParent] < size[bParent]){
			id[aParent] = bParent;
			size[bParent] += size[aParent];
		}
		else{
			id[bParent] = aParent;
			size[aParent] += size[bParent];
		}
		
		count--;
	}
	
	public int NumberOfConnectedComponents(){
		return count;	
	}
}

```
