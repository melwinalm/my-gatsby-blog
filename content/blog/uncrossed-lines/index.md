---
title: Uncrossed Lines
date: "2020-05-25"
type: problem-solving
description: Uncrossed Lines
tags: csharp
---

Note: This problem was taken from LeetCode - [Uncrossed Lines](https://leetcode.com/problems/uncrossed-lines/)

### Using Bottom Up Appraoch

```csharp
public int MaxUncrossedLines(int[] A, int[] B) {
	int a = A.Length;
	int b = B.Length;
	
	int[,] dp = new int[a+1, b+1];
	
	for(int i = 1; i <= a; i++){
		for(int j = 1; j <= b; j++){
			if(A[i-1] == B[j-1]){
				dp[i,j] = 1 + dp[i-1,j-1];
			}
			else{
				dp[i,j] = Math.Max(dp[i,j-1], dp[i-1,j]);
			}
		}
	}
	
	return dp[a,b];
}
```

### Using Bottom Up Approach (Space Optimised)

```csharp
public int MaxUncrossedLines(int[] A, int[] B) {
	int a = A.Length;
	int b = B.Length;
	
	int[] dp = new int[b+1];
	
	for(int i = 1; i <= a; i++){
		int prev = 0;            
		for(int j = 1; j <= b; j++){
			int curr = dp[j];
			if(A[i-1] == B[j-1]){
				dp[j] = 1 + prev;
			}
			else{
				dp[j] = Math.Max(dp[j], dp[j-1]);
			}
			prev = curr;
		}
	}
	
	return dp[b];
}
```

