---
title: Detect Cycles in 2D Grid
date: "2020-08-23"
type: problem-solving
description: Detect Cycles in 2D Grid
tags: csharp
---

Note: This problem was taken from LeetCode - [Detect Cycles in 2D Grid](https://leetcode.com/problems/detect-cycles-in-2d-grid/)

### Depth First Search Approach

```csharp
public bool ContainsCycle(char[][] grid) {
	int rows = grid.Length;
	
	if(rows == 0){
		return false;
	}
	
	int cols = grid[0].Length;
	
	bool[,] visited = new bool[rows,cols];
	
	for(int i = 0; i < rows; i++){
		for(int j = 0; j < cols; j++){
			if(!visited[i,j] && this.HasCycle(i, j, -1, -1, rows, cols, visited, grid)){
				return true;
			}
		}
	}
	
	return false;
}

private bool HasCycle(int curX, int curY, int lastX, int lastY, int rows, int cols, bool[,] visited, char[][] grid){
	visited[curX,curY] = true;
	
	int[] dx = new int[] {0, 1, 0, -1};
	int[] dy = new int[] {1, 0, -1, 0};
	
	for(int a = 0; a < 4; a++){
		int newX = curX + dx[a];
		int newY = curY + dy[a];
		
		// !(lastX == newX && lastY == newY) - used to prevent the dfs from going back to the previously traversed node to avoid repetition. 
		if(newX >= 0 && newX < rows && newY >= 0 && newY < cols && grid[newX][newY] == grid[curX][curY] && !(lastX == newX && lastY == newY)){
			if(visited[newX,newY] || this.HasCycle(newX, newY, curX, curY, rows, cols, visited, grid)){
				return true;
			}
		}
	}
	
	return false;
}
```
