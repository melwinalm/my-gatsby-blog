---
title: Complement of Base 10 Integer
date: "2020-10-05"
type: problem-solving
description: Complement of Base 10 Integer
tags: csharp
---

Note: This problem was taken from LeetCode - [Complement of Base 10 Integer](https://leetcode.com/problems/complement-of-base-10-integer/)

### Using Bitwise Operation

```csharp
public int BitwiseComplement(int N) {
	if(N == 0){
		return 1;
	}
	
	int power = 1;
	
	while(power <= N){
		power *= 2;
	}
	
	return power - N - 1;
}
```
