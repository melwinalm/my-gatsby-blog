---
title: Max Dot Product of Two Subsequences
date: "2020-05-24"
type: problem-solving
description: Max Dot Product of Two Subsequences
tags: csharp
---

Note: This problem was taken from LeetCode - [Max Dot Product of Two Subsequences](https://leetcode.com/problems/max-dot-product-of-two-subsequences/)

### Using Bottom Up Appraoch

```csharp
public int MaxDotProduct(int[] nums1, int[] nums2) {
	int m = nums1.Length;
	int n = nums2.Length;
	
	int[,] dp = new int[m+1,n+1];
	
	for(int i = 0; i <= m; i++){
		for(int j = 0; j <= n; j++){
			if(i == 0 || j == 0){
				dp[i,j] = Int32.MinValue;
				continue;
			}
			dp[i,j] = Math.Max(
				(nums1[i-1] * nums2[j-1]) + Math.Max(0, dp[i-1,j-1]),
				Math.Max(dp[i-1,j], dp[i,j-1])
			);
		}
	}
	
	return dp[m,n];
}
```
