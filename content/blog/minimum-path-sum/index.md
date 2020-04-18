---
title: Minimum Path Sum
date: "2020-04-18"
type: problem-solving
description: Minimum Path Sum
tags: csharp
---

Note: This problem was taken from LeetCode - [Minimum Path Sum](https://leetcode.com/problems/minimum-path-sum/)

### Recursion (Not efficient method)

```csharp
public int MinPathSum(int[][] grid) {
	int row = grid.Length;
	int col = grid[0].Length;
	
	return this.Recursion(grid, row-1, col-1);
}

public int Recursion(int[][] grid, int row, int col){
	if(row ==0 &&  col == 0){
		return grid[0][0];
	}
	else if(row == 0){
		return grid[row][col] + this.Recursion(grid, row, col - 1);
	}
	else if(col == 0){
		return grid[row][col] + this.Recursion(grid, row - 1, col);
	}
	else{
		return grid[row][col] + Math.Min(this.Recursion(grid, row - 1, col), this.Recursion(grid, row, col - 1));
	}
}
```

### Dynamic Programming

```csharp
    public int MinPathSum(int[][] grid) {
        int row = grid.Length;
        
        if(row == 0){
            return 0;
        }
        
        int col = grid[0].Length;

        for(int i = 0; i < row; i++){
            for(int j = 0; j < col; j++){
                if(i == 0 && j == 0){
                    grid[0][0] = grid[0][0];
                }
                else if(i == 0){
                    grid[i][j] = grid[i][j] + grid[i][j-1];
                }
                else if(j == 0){
                    grid[i][j] = grid[i][j] + grid[i-1][j];
                }
                else{
                    grid[i][j] = grid[i][j] + Math.Min(grid[i-1][j], grid[i][j-1]);
                }
            }
        }
        
        return grid[row-1][col-1];
    }
```

| Approach | Time Complexity | Space Complexity |
| ------------- |:-------------:| :-----:|
| Recursion | O(2^(m*n)) | stack memory is used |
| Dynamic Programming | O(m*n) | O(m*n) |
