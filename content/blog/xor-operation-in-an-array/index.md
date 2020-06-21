---
title: XOR Operation in an Array
date: "2020-06-21"
type: problem-solving
description: XOR Operation in an Array
tags: csharp
---

Note: This problem was taken from LeetCode - [XOR Operation in an Array](https://leetcode.com/problems/xor-operation-in-an-array/)

### Using Linear Solution

```csharp
public int XorOperation(int n, int start) {
	int output = start;
	
	for(int i = 1; i < n; i++){
		start += 2;
		output ^= start;
	}
	
	return output;
}
```
