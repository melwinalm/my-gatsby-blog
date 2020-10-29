---
title: Maximal Square
date: "2020-04-27"
type: problem-solving
description: Maximal Square
tags: csharp
---

Note: This problem was taken from LeetCode - [Maximal Square](https://leetcode.com/problems/maximal-square/)

### Recursion (Time Limit Exceeded)

```csharp
public int MaximalSquare(char[][] matrix) {
	int row = matrix.Length;
	
	if(row == 0){
		return 0;
	}
	
	int col = matrix[0].Length;
	
	int max = 0;
	
	for(int i = row - 1; i >= 0; i--){
		for(int j = col - 1; j >= 0; j--){
			if(matrix[i][j] == '1'){
				max = Math.Max(max, this.MaximalSquare(matrix, i, j));
			}
		}
	}
	
	return max * max;
}

public int MaximalSquare(char[][] matrix, int row, int col){
	if(row < 0 || col < 0){
		return 0;    
	}
	
	if(matrix[row][col] == '1'){
		return 1 + Math.Min(
			this.MaximalSquare(matrix, row - 1, col),
			Math.Min(
				this.MaximalSquare(matrix, row - 1, col - 1),
				this.MaximalSquare(matrix, row, col - 1)
			)
		);
	}
	
	return 0;
}
```

### Recursion with Memoization (Not really efficient)

```csharp
public int MaximalSquare(char[][] matrix) {
	int row = matrix.Length;
	
	if(row == 0){
		return 0;
	}
	
	int col = matrix[0].Length;
	
	int max = 0;
	
	int[,] memo = new int[row,col];
	
	// Initialize all the elements of the memoization array to -1
	for(int i = 0; i < row; i++){
		for(int j = 0; j < col; j++){
			memo[i,j] = -1;
		}
	}
	
	for(int i = row - 1; i >= 0; i--){
		for(int j = col - 1; j >= 0; j--){
			if(matrix[i][j] == '1'){
				max = Math.Max(max, this.MaximalSquare(matrix, i, j, memo));
			}
		}
	}
	
	return max * max;
}

public int MaximalSquare(char[][] matrix, int row, int col, int[,] memo){
	if(row < 0 || col < 0){
		return 0;    
	}
	
	if(memo[row,col] != -1){
		return memo[row,col];
	}
	
	if(matrix[row][col] == '1'){
		memo[row,col] = 1 + Math.Min(
			this.MaximalSquare(matrix, row - 1, col, memo),
			Math.Min(
				this.MaximalSquare(matrix, row - 1, col - 1, memo),
				this.MaximalSquare(matrix, row, col - 1, memo)
			)
		);
	}
	else{
		memo[row,col] = 0;
	}
	
	return memo[row,col];
}
```

### Bottom Up Approach

```csharp
public int MaximalSquare(char[][] matrix) {
	int rows = matrix.Length;
	
	if(rows == 0){
		return 0;
	}
	
	int cols = matrix[0].Length;
	
	int[,] dp = new int[rows,cols];
	
	int maxSoFar = 0;
	
	for(int i = 0; i < rows; i++){
		for(int j = 0; j < cols; j++){
			
			if(i == 0 || j == 0){
				dp[i,j] = matrix[i][j] == '1' ? 1 : 0;
			}
			else if(matrix[i][j] == '1'){
				dp[i,j] = 1 + Math.Min(Math.Min(dp[i,j-1], dp[i-1,j]), dp[i-1,j-1]);
			}
			
			maxSoFar = Math.Max(maxSoFar, dp[i,j]);
		}
	}
	
	return maxSoFar * maxSoFar;   
}
```
