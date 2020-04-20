---
title: Set Matrix Zeroes
date: "2020-04-20"
type: problem-solving
description: Set Matrix Zeroes
tags: csharp
---

Note: This problem was taken from LeetCode - [Set Matrix Zeroes](https://leetcode.com/problems/set-matrix-zeroes/)

### Not the Optimal Solution (Fails in certain edge cases)

```csharp
public void SetZeroes(int[][] matrix) {
	int row = matrix.Length;
	if(row == 0){
		return;
	}
	
	int col = matrix[0].Length;
	
	for(int i = 0; i < row; i++){
		for(int j = 0; j < col; j++){
			if(matrix[i][j] == 0){
				for(int a = 0; a < col; a++){
					if(matrix[i][a] != 0){
						matrix[i][a] = Int32.MinValue;
					}
				}
				
				for(int b = 0; b < row; b++){
					if(matrix[b][j] != 0){
						matrix[b][j] = Int32.MinValue;
					}
				}
			}
		}
	}
	
	for(int i = 0; i < row; i++){
		for(int j = 0; j < col; j++){
			if(matrix[i][j] == Int32.MinValue){
				matrix[i][j] = 0;
			}
		}
	}
	
}
```

### Better Solution

```csharp
public void SetZeroes(int[][] matrix) {
	int row = matrix.Length;
	if(row == 0){
		return;
	}
	
	int col = matrix[0].Length;
	
	bool isFirstRow = false;
	bool isFirstCol = false;
	
	// Set isFirstRow as true if there is any 0 in the first row of the matrix
	for(int i = 0; i < col; i++){
		if(matrix[0][i] == 0){
			isFirstRow = true;
			break;
		}
	}
	
	// Set isFirstCol as true if there is any 0 in the first column of the matrix
	for(int i = 0; i < row; i++){
		if(matrix[i][0] == 0){
			isFirstCol = true;
			break;
		}
	}
	
	// Iterate through the array and if a 0 is found then set the first row and column of that index to zero
	for(int i = 1; i < row; i++){
		for(int j = 1; j < col; j++){
			if(matrix[i][j] == 0){
				matrix[i][0] = 0;
				matrix[0][j] = 0;
			}
		}
	}
	
	// Iterate though the matrix again and if the first row or the column of the that element is 0 then update the current element to 0
	for(int i = 1; i < row; i++){
		for(int j = 1; j < col; j++){
			if(matrix[i][0] == 0 || matrix[0][j] == 0){
				matrix[i][j] = 0;
			}
		}
	}
	
	// If isFirstRow is true then set all the elements of the first row to zero
	if(isFirstRow){
		for(int i = 0; i < col; i++){
			matrix[0][i] = 0;
		}
	}
	
	// If isFirstCol is true then set all the elements of the first column to zero
	if(isFirstCol){
		for(int i = 0; i < row; i++){
			matrix[i][0] = 0;
		}
	}
	
}
```

| Approach | Time Complexity | Space Complexity |
| ------------- |:-------------:| :-----:|
| Not the Optimal Solution | O((m*n)*(m+n)) | O(1) |
| Better Solution | O(m*n) | O(1) |
