---
title: Smallest Integer Divisible by K
date: "2020-11-26"
type: problem-solving
description: Smallest Integer Divisible by K
tags: csharp
---

Note: This problem was taken from LeetCode - [Smallest Integer Divisible by K](https://leetcode.com/problems/smallest-integer-divisible-by-k/)

### Using Stack

```csharp
public int SmallestRepunitDivByK(int K) {
	int rem = 0;
	
	for(int N = 1; N <= K; N++){
		rem = ((rem * 10) + 1) % K;
		
		if(rem == 0){
			return N;
		}
	}
	
	return -1;
}
```
