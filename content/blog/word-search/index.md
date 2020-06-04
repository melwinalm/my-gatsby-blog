---
title: Word Search
date: "2020-06-04"
type: problem-solving
description: Word Search
tags: csharp
---

Note: This problem was taken from LeetCode - [Word Search](https://leetcode.com/problems/word-search/)

### Using Depth First Search

```csharp
public bool Exist(char[][] board, string word) {
	int rows = board.Length;
	
	if(rows == 0){
		return false;
	}
	
	int cols = board[0].Length;
	
	bool[,] visited = new bool[rows, cols];
	
	int[][] directions = new int[4][];
	directions[0] = new int[]{1,0};
	directions[1] = new int[]{0,1};
	directions[2] = new int[]{0,-1};
	directions[3] = new int[]{-1,0};
	
	for(int i = 0; i < rows; i++){
		for(int j = 0; j < cols; j++){
			bool flag = this.Search(board, word, visited, 0, i, j, rows, cols, directions);
			if(flag == true){
				return true;
			}
		}
	}
	
	return false;
}

public bool Search(char[][] board, string word, bool[,] visited, int charIndex, int rowIndex, int colIndex, int rows, int cols, int[][] directions){
	if(charIndex >= word.Length || rowIndex >= rows || colIndex >= cols || rowIndex < 0 || colIndex < 0 || visited[rowIndex,colIndex] == true){
		return false;
	}
	
	if(board[rowIndex][colIndex] != word[charIndex]){
		return false;
	}
	else{
		if(charIndex == word.Length - 1){
			return true;
		}
	}
	
	visited[rowIndex,colIndex] = true;
	
	// Recurse through all the four directions of board for the current element
	for(int i = 0; i < directions.Length; i++){            
		bool flag = this.Search(board, word, visited, charIndex+1, rowIndex + directions[i][0], colIndex + directions[i][1], rows, cols, directions);
		
		if(flag == true){
			return true;
		}            
	}
	
	// Backtracking
	visited[rowIndex,colIndex] = false;

	return false;
}
```
