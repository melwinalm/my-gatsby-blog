---
title: Dungeon Game
date: "2020-06-21"
type: problem-solving
description: Dungeon Game
tags: csharp
---

Note: This problem was taken from LeetCode - [Dungeon Game](https://leetcode.com/problems/dungeon-game/)

### Using Binary Search

For the given problem, the health can range between the values 1 and 10^9. So performing binary search for this given range can give us the minimum health required to save the pricess. But this solution may not be optimum. Check the next solution which uses dynamic programming.

### Using Bottom Up Approach

```csharp
public int CalculateMinimumHP(int[][] dungeon) {
	int rows = dungeon.Length;
	
	if(rows == 0){
		return 0;
	}
	
	int cols = dungeon[0].Length;
	
	int[,] dp = new int[rows, cols];
	
	for(int i = rows-1; i >= 0; i--){
		for(int j = cols-1; j >= 0; j--){
			// Bottom-right element
			if(i == rows-1 && j == cols - 1){
				// Min of 0 is considered whenever the health is positive, since a positive health in the future path of the knight cannot be used before that.
				dp[i,j] = Math.Min(0, dungeon[i][j]);
			}
			// Last row
			else if(i == rows-1){
				dp[i,j] = Math.Min(0, dungeon[i][j] + dp[i,j+1]);
			}
			// Last column
			else if(j == cols-1){
				dp[i,j] = Math.Min(0, dungeon[i][j] + dp[i+1,j]);
			}
			else{
				dp[i,j] = Math.Min(0, dungeon[i][j] + Math.Max(dp[i,j+1], dp[i+1,j]));
			}
		}
	}  
	
	// plus one is added to the health since we need atleast one unit greater than the min health to survive
	return Math.Abs(dp[0,0]) + 1;
}
```
