---
title: N-th Tribonacci Number
date: "2020-08-12"
type: problem-solving
description: N-th Tribonacci Number
tags: csharp
---

Note: This problem was taken from LeetCode - [N-th Tribonacci Number](https://leetcode.com/problems/n-th-tribonacci-number/)

### Using DP

```csharp
public int Tribonacci(int n) {
	int[] memo = new int[n+1];
	
	if(n == 0){
		return 0;
	}

	if(n <= 2){
		return 1;
	}
	
	memo[0] = 0;
	memo[1] = 1;
	memo[2] = 1;
	
	for(int i = 3; i <= n; i++){
		memo[i] = memo[i-1] + memo[i-2] + memo[i-3];
	}
	
	return memo[n];
}
```
