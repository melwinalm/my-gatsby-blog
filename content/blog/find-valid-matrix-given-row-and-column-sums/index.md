---
title: Find Valid Matrix Given Row and Column Sums
date: "2020-10-04"
type: problem-solving
description: Find Valid Matrix Given Row and Column Sums
tags: csharp
---

Note: This problem was taken from LeetCode - [Find Valid Matrix Given Row and Column Sums](https://leetcode.com/problems/find-valid-matrix-given-row-and-column-sums/)

### Greedy Approach

```csharp
public int[][] RestoreMatrix(int[] rowSum, int[] colSum) {
	int rows = rowSum.Length;
	int cols = colSum.Length;
	
	int[][] result = new int[rows][];
	
	for(int i = 0; i < rows; i++){
		result[i] = new int[cols];
		
		for(int j = 0; j < cols; j++){
			int val = Math.Min(rowSum[i], colSum[j]);
			
			result[i][j] = val;
			rowSum[i] -= val;
			colSum[j] -= val;
		}
	}
	
	return result;
}
```
