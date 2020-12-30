---
title: Game of Life
date: "2020-12-30"
type: problem-solving
description: Game of Life
---

Note: This problem was taken from LeetCode - [Game of Life](https://leetcode.com/problems/game-of-life/)

### m * n Solution

```csharp
public void GameOfLife(int[][] board) {
	int[] neighbors = {0, 1, -1};
	
	int rows = board.Length;
	int cols = board[0].Length;
	
	int[,] copy = new int[rows,cols];
	
	for(int i = 0; i < rows; i++){
		for(int j = 0; j < cols; j++){
			copy[i,j] = board[i][j];
		}
	}
	
	for(int row = 0; row < rows; row++){
		for(int col = 0; col < cols; col++){
			int liveNeighbors = 0;
			
			for(int i = 0; i < 3; i++){
				for(int j = 0; j < 3; j++){
					
					if(!(neighbors[i] == 0 && neighbors[j] == 0)){
						int newRow = row + neighbors[i];
						int newCol = col + neighbors[j];
						
						if(newRow >= 0 && newRow < rows && newCol >= 0 && newCol < cols && copy[newRow,newCol] == 1){
							liveNeighbors += 1;
						}
					}
				}
			}
			
			if(copy[row,col] == 1 && (liveNeighbors < 2 || liveNeighbors > 3)){
				board[row][col] = 0;
			}

			if(copy[row,col] == 0 && liveNeighbors == 3){
				board[row][col] = 1;
			}
		}
	}
}
```
