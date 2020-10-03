---
title: Longest Common Subsequence
date: "2020-04-26"
type: problem-solving
description: Longest Common Subsequence
tags: csharp
---

Note: This problem was taken from LeetCode - [Longest Common Subsequence](https://leetcode.com/problems/longest-common-subsequence/)

### Using dynamic Programming (Time limit exceeded)

```csharp
public int LongestCommonSubsequence(string text1, string text2) {
	int m = text1.Length;
	int n = text2.Length;
	
	return this.LCS(text1, text2, m-1, n-1);
}

public int LCS(string text1, string text2, int m, int n){
	if(m < 0 || n < 0){
		return 0;
	}
	
	if(text1[m] == text2[n]){
		return 1 + this.LCS(text1, text2, m-1, n-1);
	}
	else{
		return Math.Max(this.LCS(text1, text2, m-1, n), this.LCS(text1, text2, m, n-1));
	}
}
```

### Using DP with memoization (Time limit exceeded)

```csharp
public int LongestCommonSubsequence(string text1, string text2) {
	int m = text1.Length;
	int n = text2.Length;
	
	int[,] memo = new int[m,n];
	
	return this.LCS(text1, text2, m-1, n-1, memo);
}

public int LCS(string text1, string text2, int m, int n, int[,] memo){
	if(m < 0 || n < 0){
		return 0;
	}
	
	if(text1[m] == text2[n]){
		memo[m,n] = 1 + this.LCS(text1, text2, m-1, n-1, memo);
	}
	else{
		memo[m,n] = Math.Max(this.LCS(text1, text2, m-1, n, memo), this.LCS(text1, text2, m, n-1, memo));
	}
	
	return memo[m,n];
}
```

### Bottom Up Approach

```csharp
public int LongestCommonSubsequence(string text1, string text2) {
	int m = text1.Length;
	int n = text2.Length;
	
	int[,] dp = new int[m+1,n+1];
	
	for(int i = 1; i <= m; i++){
		for(int j = 1; j <= n; j++){
			if(text1[i-1] == text2[j-1]){
				dp[i,j] = 1 + dp[i-1,j-1];
			}
			else{
				dp[i,j] = Math.Max(dp[i-1,j], dp[i,j-1]);
			}
		}
	}
	
	return dp[m,n];
}
```

### Bottom Up Approach (Space Optimised)

```csharp
public int LongestCommonSubsequence(string text1, string text2) {
	int m = text1.Length;
	int n = text2.Length;
	
	int[] dp = new int[m+1];
	int[] prev = new int[m+1];
	
	// Scan through all rows and then through all columns 
	for(int j = 1; j <= n; j++){
		for(int i = 1; i <= m; i++){
			if(text1[i-1] == text2[j-1]){
				dp[i] = 1 + prev[i-1];
			}
			else{
				dp[i] = Math.Max(dp[i-1], prev[i]);
			}
		}
		prev = (int[])dp.Clone(); // Copy array without reference
	}
	
	return prev[m];
}
```
