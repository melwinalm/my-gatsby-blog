---
title: Hamming Distance
date: "2020-03-29"
type: problem-solving
description: Hamming Distance
tags: csharp
---

Note: This problem was taken from LeetCode - [Hamming Distance](https://leetcode.com/problems/hamming-distance/)

### Using Bitwise Operations

Performing an XOR operation between the given two numbers will return you a new binary number with the bits set to 1 wherever the corresponding bits are different. Now take this number and `AND` it with 1. This will give you 1 if the LSB is 1 else it will return you zero. Add this number to a `count` variable. Now right shift the number by 1 bit and repeat this operation. Keep doing this until the number is zero. In the end, the count value is the Hamming Distance of the given two numbers.

```csharp
public int HammingDistance(int x, int y) {
	int z = x ^ y;
	
	int count = 0;
	while(z != 0){
		count += z & 1;
		z = z >> 1;
	}
	
	return count;
}
```
