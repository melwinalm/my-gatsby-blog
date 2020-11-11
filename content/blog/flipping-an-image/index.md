---
title: Flipping an Image
date: "2020-11-11"
type: problem-solving
description: Flipping an Image
tags: csharp
---

Note: This problem was taken from LeetCode - [Flipping an Image](https://leetcode.com/problems/flipping-an-image/)

### Naive Approach

```csharp
public int[][] FlipAndInvertImage(int[][] A) {
	int rows = A.Length;
	
	if(rows == 0){
		return A;
	}
	
	int cols = A[0].Length;
	
	for(int i = 0; i < rows; i++){
		for(int j = 0; j < (cols+1)/2; j++){
			int temp = this.Inv(A[i][j]);
			A[i][j] = this.Inv(A[i][cols-j-1]);
			A[i][cols-j-1] = temp;
		}
	}
	
	return A;
}

public int Inv(int a){
	return a == 1 ? 0 : 1; // Can use return a ^ 1 also
}
```
