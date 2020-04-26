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
	return this.LCS(text1, text2, text1.Length - 1, text2.Length - 1);
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
	int[,] dp = new int[text1.Length, text2.Length];
	return this.LCS(text1, text2, text1.Length - 1, text2.Length - 1, dp);
}

public int LCS(string text1, string text2, int m, int n, int[,] dp){
	if(m < 0 || n < 0){
		return 0;
	}
	
	if(text1[m] == text2[n]){
		dp[m,n] = 1 + this.LCS(text1, text2, m-1, n-1, dp);
	}
	else{
		dp[m,n] = Math.Max(this.LCS(text1, text2, m-1, n, dp), this.LCS(text1, text2, m, n-1, dp));
	}
	
	return dp[m,n];
}
```

### Bottom Up Approach

```csharp
public int LongestCommonSubsequence(string text1, string text2) {
	int[,] dp = new int[text1.Length + 1, text2.Length + 1];
	
	for(int i = 0; i <= text1.Length; i++){
		for(int j = 0; j <= text2.Length; j++){
			if(i == 0 || j == 0){
				dp[i,j] = 0;
			}
			else if(text1[i-1] == text2[j-1]){
				dp[i,j] = 1 + dp[i-1,j-1];
			}
			else{
				dp[i,j] = Math.Max(dp[i-1,j], dp[i,j-1]);
			}
		}
	}
	
	return dp[text1.Length, text2.Length];
    }
```
