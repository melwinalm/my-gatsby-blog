---
title: Reverse Bits
date: "2020-07-12"
type: problem-solving
description: Reverse Bits
tags: csharp
---

Note: This problem was taken from LeetCode - [Reverse Bits](https://leetcode.com/problems/reverse-bits/)

### Using Bitwise Operations

```csharp
public uint reverseBits(uint n) {
	uint output = 0;
	
	for(int i = 0; i < 32; i++){
		output <<= 1;
		if((n&1) == 1){
			output++;
		}
		n >>= 1;
	}
	
	return output;
}
```
