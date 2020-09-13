---
title: Special Positions in a Binary Matrix
date: "2020-09-13"
type: problem-solving
description: Special Positions in a Binary Matrix
tags: csharp
---

Note: This problem was taken from LeetCode - [Special Positions in a Binary Matrix](https://leetcode.com/problems/special-positions-in-a-binary-matrix/)

### Using 2-Pass

```csharp
public int NumSpecial(int[][] mat) {
	int rows = mat.Length;
	
	if(rows == 0){
		return 0;
	}
	
	int cols = mat[0].Length;
	
	int[] rowCount = new int[rows];
	int[] colCount = new int[cols];
	
	for(int i = 0; i < rows; i++){
		for(int j = 0; j < cols; j++){
			if(mat[i][j] == 1){
				rowCount[i] += 1;
				colCount[j] += 1;
			}
		}
	}
	
	int output = 0;
	
	for(int i = 0; i < rows; i++){
		for(int j = 0; j < cols; j++){
			if(mat[i][j] == 1 && rowCount[i] == 1 && colCount[j] == 1){
				output++;
			}
		}
	}
	
	return output;
}
```
