---
title: Permutation Sequence
date: "2020-06-21"
type: problem-solving
description: Permutation Sequence
tags: csharp
---

Note: This problem was taken from LeetCode - [Permutation Sequence](https://leetcode.com/problems/permutation-sequence/)

### Using Iterative Approach

```csharp
public string GetPermutation(int n, int k) {
	int[] fact = new int[n];
	
	fact[0] = 1;
	for(int i = 1; i < n ; i++){
		fact[i] = fact[i-1] * i;
	}
	
	List<int> map = new List<int>();
	for(int i = 0; i < n; i++){
		map.Add(i+1);
	}
	
	string output = "";
	k--;
	
	for(int i = n; i > 0; i--){
		int index = k / fact[i-1];
		k = k % fact[i-1];
		output += map[index];
		map.RemoveAt(index);
	}
	
	return output;
}
```
