---
title: Ugly Number II
date: "2020-07-04"
type: problem-solving
description: Ugly Number II
tags: csharp
---

Note: This problem was taken from LeetCode - [Ugly Number II](https://leetcode.com/problems/ugly-number-ii/)

### Using Dynamic programming

```csharp
public int NthUglyNumber(int n) {
	int[] dp = new int[n];
	
	dp[0] = 1;
	
	int index2 = 0;
	int index3 = 0;
	int index5 = 0;
	
	int factor2 = 2;
	int factor3 = 3;
	int factor5 = 5;
	
	dp[0] = 1;
	
	for(int i = 1; i < n; i++){
		dp[i] = Math.Min(Math.Min(factor2, factor3), factor5);
		
		if(factor2 == dp[i]){
			index2++;
			factor2 = 2*dp[index2];
		}
		
		if(factor3 == dp[i]){
			index3++;
			factor3 = 3*dp[index3];
		}
		
		if(factor5 == dp[i]){
			index5++;
			factor5 = 5*dp[index5];
		}
	}
	
	return dp[n-1];
}
```
