---
title: Dungeon Game
date: "2020-06-21"
type: problem-solving
description: Dungeon Game
tags: csharp
---

Note: This problem was taken from LeetCode - [Dungeon Game](https://leetcode.com/problems/dungeon-game/)

### Using Bottom Up Approach

```csharp
public int CalculateMinimumHP(int[][] dungeon) {
	int rows = dungeon.Length;
	
	if(rows == 0){
		return 0;
	}
	
	int cols = dungeon[0].Length;
	
	int[,] dp = new int[rows+1, cols+1];
	
  // Filling the dp array with default values
	for(int i = 0; i <= rows; i++){
		for(int j = 0; j <= cols; j++){
			dp[i,j] = Int32.MaxValue;
		}
	}
	
	dp[rows, cols-1] = 1;
	dp[rows-1, cols] = 1;
	
	for(int i = rows - 1; i >= 0; i--){
		for(int j = cols-1; j >= 0; j--){
			int req = Math.Min(dp[i, j+1], dp[i+1,j]) - dungeon[i][j];
			dp[i,j] = req <=0 ? 1 : req;
		}
	}
	
	return dp[0,0];
}
```
