---
title: Search a 2D Matrix II
date: "2020-06-27"
type: problem-solving
description: Search a 2D Matrix II
tags: csharp
---

Note: This problem was taken from LeetCode - [Search a 2D Matrix II](https://leetcode.com/problems/search-a-2d-matrix-ii/)

### Using Divide and Conquer (Time Limit exceeded)

```csharp
public bool SearchMatrix(int[,] matrix, int target) {
	int rows = matrix.GetLength(0);
	int cols = matrix.GetLength(1);
	
	if(rows == 0 && cols == 0){
		return false;
	}
   
	return this.DivideAndConquer(matrix, 0, rows-1, 0, cols-1, target);        
}

public bool DivideAndConquer(int[,] matrix, int rStart, int rEnd, int cStart, int cEnd, int target){
	if(rStart > rEnd || cStart > cEnd){
		return false;
	}
	
	if(rStart == rEnd && cStart == cEnd){
		return target == matrix[rStart,cStart] ? true : false;
	}
	
	int rMid = (rStart + rEnd)/2;
	int cMid = (cStart + cEnd)/2;
	
	return this.DivideAndConquer(matrix, rStart, rMid, cStart, cMid, target)
		|| this.DivideAndConquer(matrix, rMid+1, rEnd, cStart, cMid, target)
		|| this.DivideAndConquer(matrix, rStart, rMid, cMid+1, cEnd, target)
		|| this.DivideAndConquer(matrix, rMid+1, rEnd, cMid+1, cEnd, target);
}
```

### Using (m+n) solution

```csharp
public bool SearchMatrix(int[,] matrix, int target) {
	int row = 0;
	int col = matrix.GetLength(1)-1;
	
	while(col >= 0 && row < matrix.GetLength(0)){
		if(target == matrix[row,col]){
			return true;
		}
		else if(target < matrix[row,col]){
			col--;
		}
		else{
			row++;
		}
	}
	
	return false;
}
```

### Using Binary Seach (mlogn or nlogm solution)

This method performs binary seach on each row(or column) to find the element.

```csharp
public bool SearchMatrix(int[,] matrix, int target) {
	int rows = matrix.GetLength(0);
	int cols = matrix.GetLength(1);
	
	if(rows == 0  && cols == 0){
		return false;
	}
	
	for(int i = 0; i < rows; i++){
		
		int low = 0;
		int high = cols-1;
		
		while(low <= high){
			int mid = (low+high)/2;
			
			if(target == matrix[i,mid]){
				return true;
			}
			else if(target < matrix[i,mid]){
				high = mid-1;
			}
			else{
				low = mid+1;
			}
		}
	}
	
	return false;
}
```
