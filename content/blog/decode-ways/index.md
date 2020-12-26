---
title: Decode Ways
date: "2020-12-26"
type: problem-solving
description: Decode Ways
---

Note: This problem was taken from LeetCode - [Decode Ways](https://leetcode.com/problems/decode-ways/)

### Using Dynamic Programming (Top Down)

```csharp
public int NumDecodings(string s) {
	int N = s.Length;
	if(N == 0){
		return 0;
	}
	
	int[] dp = new int[N+1];
	dp[N] = 1;
	dp[N-1] = s[N-1] != '0' ? 1 : 0;
	
	for(int i = N-2; i >= 0; i--){
		if(s[i] == '0'){
			continue;
		}
		else{
			dp[i] = Convert.ToInt32(s.Substring(i, 2)) <= 26 ? dp[i+1] + dp[i+2] : dp[i+1];                
		}
	}
	
	return dp[0];
}
```
