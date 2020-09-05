---
title: Matrix Diagonal Sum
date: "2020-09-05"
type: problem-solving
description: Matrix Diagonal Sum
tags: csharp
---

Note: This problem was taken from LeetCode - [Matrix Diagonal Sum](https://leetcode.com/problems/matrix-diagonal-sum/)

### Linear Approach

```csharp
public int DiagonalSum(int[][] mat) {
	int n = mat.Length;
	
	if(n == 0){
		return 0;
	}
	
	int sum = 0;

	for(int i = 0; i < n; i++){
		sum += mat[i][i] + mat[i][n-i-1];
	}
	
	if(n % 2 == 1){
		sum -= mat[n/2][n/2];
	}
	
	return sum;
}
```
