---
title: Count Square Submatrices with All Ones
date: "2020-05-11"
type: problem-solving
description: Count Square Submatrices with All Ones
tags: csharp
---

Note: This problem was taken from LeetCode - [Count Square Submatrices with All Ones](https://leetcode.com/problems/count-square-submatrices-with-all-ones/)

### Using Bottom-Up Approach

```csharp
    public int CountSquares(int[][] matrix) {
        int row = matrix.Length;
        
        if(row == 0){
            return 0;
        }
        
        int col = matrix[0].Length;
        
        int[,] dp = new int[row+1, col+1];
        
        int count = 0;
        
        for(int i = 1; i <= row; i++){
            for(int j = 1; j <= col; j++){
                if(matrix[i-1][j-1] == 1){                
                    dp[i,j] = Math.Min(dp[i-1,j], Math.Min(dp[i,j-1], dp[i-1,j-1])) + 1;
                    count += dp[i,j];
                }
            }
        }
        
        return count;        
    }
```
