---
title: Delete Operation for Two Strings
date: "2020-10-03"
type: problem-solving
description: Delete Operation for Two Strings
tags: csharp
---

Note: This problem was taken from LeetCode - [Delete Operation for Two Strings](https://leetcode.com/problems/delete-operation-for-two-strings/)

### Top Down Approach (Time Limit Exceeded)

```csharp
public int MinDistance(string word1, string word2) {
	int m = word1.Length;
	int n = word2.Length;
	
	if(m == 0 || n == 0){
		return Math.Max(m,n);
	}
	
	return m + n - 2 * this.MinSteps(word1, word2, m-1, n-1);        
}

public int MinSteps(string word1, string word2, int m, int n){
	if(m < 0 || n < 0){
		return 0;
	}
	
	if(word1[m] == word2[n]){
		return 1 + this.MinSteps(word1, word2, m-1, n-1);
	}
	else{
		return Math.Max(this.MinSteps(word1, word2, m-1, n), this.MinSteps(word1, word2, m, n-1));
	}
}
```

### Top Down Approach (using Memoization) (Time Limit Exceeded)

```csharp
public int MinDistance(string word1, string word2) {
	int m = word1.Length;
	int n = word2.Length;
	
	if(m == 0 || n == 0){
		return Math.Max(m,n);
	}
	
	int[,] memo = new int[m,n];
	
	return m + n - 2 * this.MinSteps(word1, word2, m-1, n-1, memo);        
}

public int MinSteps(string word1, string word2, int m, int n, int[,] memo){
	if(m < 0 || n < 0){
		return 0;
	}
	
	if(word1[m] == word2[n]){
		memo[m,n] = 1 + this.MinSteps(word1, word2, m-1, n-1, memo);
	}
	else{
		memo[m,n] = Math.Max(this.MinSteps(word1, word2, m-1, n, memo), this.MinSteps(word1, word2, m, n-1, memo));
	}
	
	return memo[m,n];
}
```

### Bottom Up Approach

```csharp
public int MinDistance(string word1, string word2) {
	int m = word1.Length;
	int n = word2.Length;
	
	int[,] dp = new int[m+1,n+1];
	
	for(int i = 1; i <= m; i++){
		for(int j = 1; j <= n; j++){
			if(word1[i-1] == word2[j-1]){
				dp[i,j] = 1 + dp[i-1,j-1];
			}
			else{
				dp[i,j] = Math.Max(dp[i-1,j], dp[i,j-1]);
			}
		}
	}
	
	return m + n - 2 * dp[m,n];
}
```

### Bottom Up Approach (Space Optimised)

```csharp
public int MinDistance(string word1, string word2) {
	int m = word1.Length;
	int n = word2.Length;
	
	int[] dp = new int[n+1];
	int[] prev = new int[n+1];
	
	for(int i = 1; i <= m; i++){
		for(int j = 1; j <= n; j++){
			if(word1[i-1] == word2[j-1]){
				dp[j] = 1 + prev[j-1];
			}
			else{
				dp[j] = Math.Max(prev[j], dp[j-1]);
			}
		}
		prev = (int[])dp.Clone();
	}
	
	return m + n - 2 * dp[n];
}
```
