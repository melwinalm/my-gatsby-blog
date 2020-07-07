---
title: Island Perimeter
date: "2020-07-07"
type: problem-solving
description: Island Perimeter
tags: csharp
---

Note: This problem was taken from LeetCode - [Island Perimeter](https://leetcode.com/problems/island-perimeter/)

### Using Naive Approach

```csharp
public int IslandPerimeter(int[][] grid) {
	int rows = grid.Length;
	
	if(rows == 0){
		return 0;
	}
	
	int cols = grid[0].Length;
	
	int count = 0;

	for(int i = 0; i < rows; i++){
		for(int j = 0; j < cols; j++){
			if(grid[i][j] == 1){
				count += this.Perimeter(grid, i, j, rows, cols);
			}
		}
	}
	
	
	return count;
}

public int Perimeter(int[][] grid, int i, int j, int rows, int cols){
	int count = 0;
	
	if(i == 0){
		count++;
	}
	
	if(i == rows-1){
		count++;
	}
	
	if(j == 0){
		count++;
	}
	
	if(j == cols-1){
		count++;
	}
	
	if(i > 0 && grid[i-1][j] == 0){
		count++;
	}
	
	if(i < rows-1 && grid[i+1][j] == 0){
		count++;
	}

	if(j > 0 && grid[i][j-1] == 0){
		count++;
	}
	
	if(j < cols-1 && grid[i][j+1] == 0){
		count++;
	}
	
	return count;
}
```


### Using Depth First Search

```csharp
public int IslandPerimeter(int[][] grid) {
	int rows = grid.Length;
	
	if(rows == 0){
		return 0;
	}
	
	int cols = grid[0].Length;
	
	bool[,] visited = new bool[rows, cols];
	
	int[] dirR = new int[]{0, 0, 1, -1};
	int[] dirC = new int[]{1, -1, 0, 0};
	
	for(int i = 0; i < rows; i++){
		for(int j = 0; j < cols; j++){
			if(grid[i][j] == 1){
				return this.DFS(grid, i, j, rows, cols, visited, dirR, dirC);
			}
		}
	}
	
	return 0;
}

public int DFS(int[][] grid, int i, int j, int rows, int cols, bool[,] visited, int[] dirR, int[] dirC){
	if(i < 0 || j < 0 || i >= rows || j >= cols){
		return 1;
	}
	
	if(visited[i,j] == true){
		return 0;
	}
	
	if(grid[i][j] == 0){
		return 1;
	}
	
	visited[i,j] = true;
	
	int count = 0;
	
	for(int a = 0; a < 4; a++){
		int newI = i + dirR[a];
		int newJ = j + dirC[a];
		
		count += this.DFS(grid, newI, newJ, rows, cols, visited, dirR, dirC);
	}
	
	return count;        
}
```
