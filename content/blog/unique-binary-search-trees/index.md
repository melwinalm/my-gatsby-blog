---
title: Unique Binary Search Trees
date: "2020-06-24"
type: problem-solving
description: Unique Binary Search Trees
tags: csharp
---

Note: This problem was taken from LeetCode - [Unique Binary Search Trees](https://leetcode.com/problems/unique-binary-search-trees/)

### Using Dynamic Programming

```csharp
public int NumTrees(int n) {
	int[] memo = new int[n+1];
	memo[0] = 1;
	memo[1] = 1;
	
	for(int i = 2; i <=n; i++){
		for(int j = 1; j <= i; j++){
			memo[i] += memo[i-j] * memo[j-1];
		}
	}
	
	return memo[n];
}
```

### Using Catalan Number

Use this formula to get the result - (2n)!/((n+1)!*n!) 
