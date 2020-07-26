---
title: Shuffle String
date: "2020-07-23"
type: problem-solving
description: Shuffle String
tags: csharp
---

Note: This problem was taken from LeetCode - [Shuffle String](https://leetcode.com/problems/shuffle-string/)

### Using Naive Approach

```csharp
public string RestoreString(string s, int[] indices) {
	int N = s.Length;
	
	char[] output = new char[N];
	
	for(int i = 0; i < N ; i++){
		output[indices[i]] = s[i];
	}
	
	return new string(output);
}
```
