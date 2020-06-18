---
title: Surrounded Regions
date: "2020-06-18"
type: problem-solving
description: Surrounded Regions
tags: csharp
---

Note: This problem was taken from LeetCode - [Surrounded Regions](https://leetcode.com/problems/surrounded-regions/)

### Using Depth First Search

```csharp
public void Solve(char[][] board) {
	int rows = board.Length;
	
	if(rows == 0){
		return;
	}
	
	int cols = board[0].Length;
	
	bool[,] visited = new bool[rows,cols];
	
	// Direction vectors for the DFS to traverse
	int[] dirR = new int[]{0,0,1,-1};
	int[] dirC = new int[]{1,-1,0,0};
	
	// Search through all the O's on the border of the matrix and perform DFS on all the borders where it is O
	for(int i = 0; i < rows; i++){
		for(int j = 0; j < cols; j++){
			if(i == 0 || j == 0 || i == rows-1 || j == cols-1){
				if(board[i][j] == 'O' && visited[i,j] == false){
					this.BorderDFS(board, visited, i, j, rows, cols, dirR, dirC);
				}
			}
		}
	}
	
	// Turn all the O's to X which are not visited
	for(int i = 0; i < rows; i++){
		for(int j = 0; j < cols; j++){
			if(i > 0 && j > 0 && i < rows && j < cols){
				if(board[i][j] == 'O' && visited[i,j] == false){
					board[i][j] = 'X';
				}
			}
		}
	}
}

public void BorderDFS(char[][] board, bool[,] visited, int i, int j, int rows, int cols, int[] dirR, int[] dirC){
	if(i < 0 || j < 0 || i >= rows || j >= cols || visited[i,j] == true || board[i][j] == 'X'){
		return;
	}
	
	visited[i,j] = true;
	
	for(int a = 0; a < dirR.Length; a++){
		this.BorderDFS(board, visited, i + dirR[a], j + dirC[a], rows, cols, dirR, dirC);
	}
}
```
