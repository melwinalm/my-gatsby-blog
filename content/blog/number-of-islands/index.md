---
title: Number of Islands
date: "2020-04-01"
type: problem-solving
description: Number of Islands
tags: csharp
---

Note: This problem was taken from LeetCode - [Number of Islands](https://leetcode.com/problems/number-of-islands/)

### Depth First Search

Perform a DFS on all the nodes in the given grid. Each time a node is visited update the node value to `V` as in visited. This is done to prevent the islands from being counted twice. 

```csharp
public int NumIslands(char[][] grid) {   
	int maxRow = grid.Length;
	
	// Edge case to check if the grid is of size 0x0 
	if(maxRow == 0){
		return 0;
	}
	
	int maxCol = grid[0].Length;
	
	int count = 0;
	
	for(int i = 0; i < maxRow; i++){
		for(int j = 0; j < maxCol; j++){
			if(grid[i][j] == '1'){
				this.DFS(grid, i, j, maxRow, maxCol);
				count++;
			}
		}
	}

	return count;
}

public void DFS(char[][] grid, int row, int col, int maxRow, int maxCol){
	// Validating if the given row and col indexes are in the grid range
	if(row < 0 || row >= maxRow || col < 0 || col >= maxCol || grid[row][col] != '1'){
		return;
	}
	
	grid[row][col] = 'V';
	
	// For a row and column index recursively call the DFS function on the neighbouring nodes i.e. (-1, 0), (0, -1), (1, 0), (0, 1)
	this.DFS(grid, row+1, col, maxRow, maxCol);
	this.DFS(grid, row-1, col, maxRow, maxCol);
	this.DFS(grid, row, col+1, maxRow, maxCol);
	this.DFS(grid, row, col-1, maxRow, maxCol);
}
```
