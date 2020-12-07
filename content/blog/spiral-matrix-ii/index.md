---
title: Spiral Matrix II
date: "2020-12-07"
type: problem-solving
description: Spiral Matrix II
tags: csharp
---

Note: This problem was taken from LeetCode - [Spiral Matrix II](https://leetcode.com/problems/spiral-matrix-ii/)

### Naive Solution

```csharp
public int[][] GenerateMatrix(int n) {
	int[][] output = new int[n][];
	
	for(int i = 0; i < n; i++){
		output[i] = new int[n];
	}
	
	int num = 1;
	int top = 0;
	int bottom = n-1;
	int left = 0;
	int right = n-1;
	
	while(left <= right && top <= bottom){
		for(int i = left; i <= right && top <= bottom && left <= right; i++){
			output[top][i] = num;
			num++;
		}
		top++;
		
		for(int i = top; i <= bottom && top <= bottom && left <= right; i++){
			output[i][right] = num;
			num++;
		}
		right--;
		
		for(int i = right; i >= left && top <= bottom && left <= right; i--){
			output[bottom][i] = num;
			num++;
		}
		bottom--;
		
		for(int i = bottom; i >= top && top <= bottom && left <= right; i--){
			output[i][left] = num;
			num++;
		}
		left++;
		
	}
	
	return output;
}
```
