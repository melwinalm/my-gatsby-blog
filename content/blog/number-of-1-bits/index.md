---
title: Number of 1 Bits
date: "2020-04-01"
type: problem-solving
description: Number of 1 Bits
tags: csharp
---

Note: This problem was taken from LeetCode - [Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits/)

### Bitwise Operation

Simply `AND` the given number by 1. If the LSB was 1 then the `AND` operation will return you 1, else 0. Right shift the number by 1 bit and keep repeating this to get the hamming distance.

```csharp
public int HammingWeight(uint n) {
	int count = 0;
	
	while(n > 0){
		count += (int)(n & 1);
		n = n >> 1;
	}
	
	return count;
}
```
