---
title: Unique Paths
date: "2020-05-09"
type: problem-solving
description: Unique Paths
tags: csharp
---

Note: This problem was taken from LeetCode - [Unique Paths](https://leetcode.com/problems/unique-paths/)

### Using Bottom Up Approach

```csharp
public int UniquePaths(int m, int n) {
	int[,] dp = new int[m,n];
	
	for(int i = 0; i < m; i++){
		dp[i,0] = 1;
	}
	
	for(int i = 0; i < n; i++){
		dp[0,i] = 1;
	}
	
	for(int i = 1; i < m; i++){
		for(int j = 1; j < n; j++){
			dp[i,j] = dp[i-1,j] + dp[i,j-1];
		}
	}
	
	return dp[m-1,n-1];
}
```

### Using Bottom Up Approach (Space Optimized)

```csharp
public int UniquePaths(int m, int n) {
	int a = Math.Min(m,n);
	int b = Math.Max(m,n);
	
	int[] dp = new int[a];
	
	for(int i = 0; i < a; i++){
		dp[i] = 1;
	}

	for(int i = 1; i < b; i++){
		for(int j = 1; j < a; j++){
			dp[j] += dp[j-1]; 
		}
	}
	
	return dp[a-1];
}
```

### Using Formula

```
ans = (a + b)!/(a! * b!) where a = m-1 and b = n-1
```
