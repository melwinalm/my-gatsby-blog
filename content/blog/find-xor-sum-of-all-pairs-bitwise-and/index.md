---
title: Find XOR Sum of All Pairs Bitwise AND
date: "2021-04-18"
type: problem-solving
description: Find XOR Sum of All Pairs Bitwise AND
tags: csharp
---

Note: This problem was taken from LeetCode - [Find XOR Sum of All Pairs Bitwise AND](https://leetcode.com/problems/find-xor-sum-of-all-pairs-bitwise-and/)

### Using Distributive Property

```csharp
public int GetXORSum(int[] arr1, int[] arr2) {
	int xorA = 0;
	int xorB = 0;
	
	foreach(int num in arr1){
		xorA ^= num;
	}
	
	foreach(int num in arr2){
		xorB ^= num;
	}
	
	return xorA & xorB;
}
```
