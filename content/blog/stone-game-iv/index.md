---
title: Stone Game IV
date: "2020-11-05"
type: problem-solving
description: Stone Game IV
tags: csharp
---

Note: This problem was taken from LeetCode - [Stone Game IV](https://leetcode.com/problems/stone-game-iv/)

### Bottom Up Approach

```csharp
public bool WinnerSquareGame(int n) {
	bool[] dp = new bool[n+1];
	
	for(int i = 0; i < n+1; i++){
		for(int k = 1; k * k <= i; k++){
			if(dp[i - k*k] == false){
				dp[i] = true;
				break;
			}
		}
	}
	
	return dp[n];
}
```
