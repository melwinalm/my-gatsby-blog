---
title: Counting Bits
date: "2020-05-28"
type: problem-solving
description: Counting Bits
tags: csharp
---

Note: This problem was taken from LeetCode - [Counting Bits](https://leetcode.com/problems/counting-bits/)

### Bitwise Solution

```csharp
public int[] CountBits(int num) {
	int[] output = new int[num + 1];
	output[0]= 0;
	
	for(int i = 1; i <= num; i++){
		// For even numbers 1000(8) will be same as 100(4)
		if(i % 2 == 0){
			output[i] = output[i>>1];
		}
		// For odd numbers 111(7) will be same as 1 + 110(6)
		else{
			output[i] = output[i-1] + 1;
		}
	}
	
	return output;
}
```
