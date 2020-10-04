---
title: Shortest Path in Binary Matrix
date: "2020-10-04"
type: problem-solving
description: Shortest Path in Binary Matrix
tags: csharp
---

Note: This problem was taken from LeetCode - [Shortest Path in Binary Matrix](https://leetcode.com/problems/shortest-path-in-binary-matrix/)

### Using DFS (Time Limit Exceeded)

```csharp
public int ShortestPathBinaryMatrix(int[][] grid) {
	int[] dirR = new int[] {-1, -1, -1, 0, 1, 1,  1,  0};
	int[] dirC = new int[] {-1,  0,  1, 1, 1, 0, -1, -1};
	
	int rows = grid.Length;
	
	if(rows == 0){
		return 0;
	}
	
	int cols = grid[0].Length;
	
	int val = this.DFS(grid, dirR, dirC, rows-1, cols-1, new HashSet<string>(), rows, cols);
	
	return val >= 10000 ? -1 : val;
}

public int DFS(int[][] grid, int[] dirR, int[] dirC, int i, int j, HashSet<string> visited, int rows, int cols){
	string path = i.ToString() + "%" + j.ToString();
	
	if(i < 0 || j < 0 || i >= rows || j >= cols || visited.Contains(path) || grid[i][j] == 1){
		return 10000;
	}
	
	if(i == 0 && j == 0){
		return 1;
	}
	
	visited.Add(path);
	
	int minVal = 10000;
	for(int a = 0; a < 8; a++){
		int newI = i + dirR[a];
		int newJ = j + dirC[a];
		
		minVal = Math.Min(minVal, this.DFS(grid, dirR, dirC, newI, newJ, visited, rows, cols));
	}
	
	visited.Remove(path);
	
	return 1 + minVal;
}
```

### Using BFS

```csharp
public int ShortestPathBinaryMatrix(int[][] grid) {
	int[] dirR = new int[] {-1, -1, -1, 0, 1, 1,  1,  0};
	int[] dirC = new int[] {-1,  0,  1, 1, 1, 0, -1, -1};
	
	int rows = grid.Length;
	
	if(rows == 0){
		return 0;
	}
	
	int cols = grid[0].Length;
	
	if(grid[0][0] == 1 || grid[rows-1][cols-1] == 1){
		return -1;
	}
	
	bool[,] visited = new bool[rows,cols];
	visited[0,0] = true;
	
	Queue<int[]> bfsQueue = new Queue<int[]>();
	bfsQueue.Enqueue(new int[]{0,0});
	
	int output = 0;
	
	while(bfsQueue.Count > 0){
		int count = bfsQueue.Count;
		
		for(int i = 0; i < count; i++){
			int[] curr = bfsQueue.Dequeue();
			
			if(curr[0] == rows-1 && curr[1] == cols-1){
				return output + 1;  
			}
			
			for(int a = 0; a < 8; a++){
				int newI = curr[0] + dirR[a];
				int newJ = curr[1] + dirC[a];
				
				if(newI >= 0 && newJ >= 0 && newI < rows && newJ < cols && !visited[newI,newJ] && grid[newI][newJ] == 0){
					bfsQueue.Enqueue(new int[] {newI, newJ});
					visited[newI,newJ] = true;
				}
				
			}
		}
		output++;
	}
	
	return -1;
}
```
