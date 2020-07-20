---
title: Range Sum Query 2D - Immutable
date: "2020-07-20"
type: problem-solving
description: Range Sum Query 2D - Immutable
tags: csharp
---

Note: This problem was taken from LeetCode - [Range Sum Query 2D - Immutable](https://leetcode.com/problems/range-sum-query-2d-immutable/)

### Using Bottom Up Approach

```csharp
int[,] range;
public NumMatrix(int[][] matrix) {
	int rows = matrix.Length;
	if(rows == 0){
		range = new int[0,0];
		return;
	}
	
	int cols = matrix[0].Length;
	
	range = new int[rows+1, cols+1];
	
	for(int i = 1; i <= rows; i++){
		for(int j = 1; j <= cols; j++){
			range[i,j] = matrix[i-1][j-1] + range[i-1,j] + range[i,j-1] - range[i-1,j-1];
		}
	}
	
}

public int SumRegion(int row1, int col1, int row2, int col2) {
	return range[row2+1, col2+1] - range[row2+1,col1] - range[row1,col2+1] + range[row1,col1];
}
```
