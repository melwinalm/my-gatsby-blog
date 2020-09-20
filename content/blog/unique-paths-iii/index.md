---
title: Unique Paths III
date: "2020-09-20"
type: problem-solving
description: Unique Paths III
tags: csharp
---

Note: This problem was taken from LeetCode - [Unique Paths III](https://leetcode.com/problems/unique-paths-iii/)

### Using DFS with Backtracking

```csharp
public class Solution {
    int count = 0;
    int visitCount = 0;
    
    public int UniquePathsIII(int[][] grid) {
        int rows = grid.Length;
        
        if(rows == 0){
            return 0;
        }
        
        int cols = grid[0].Length;
        
        int startR = 0;
        int startC = 0;
        
        for(int i = 0; i < rows; i++){
            for(int j = 0; j < cols; j++){
                if(grid[i][j] == 1 || grid[i][j] == 0){
                    visitCount++;
                }
                
                if(grid[i][j] == 1){
                    startR = i;
                    startC = j;
                }
            }
        }
        
        this.Traverse(grid, startR, startC, new HashSet<string>(), rows, cols);
        
        return count;
    }
    
    public void Traverse(int[][] grid, int i, int j, HashSet<string> visited, int rows, int cols){
        string loc = i.ToString() + "$" + j.ToString();
        
        if(i < 0 || j < 0 || i >= rows || j >= cols || grid[i][j] == -1 || visited.Contains(loc)){
            return;
        }
        
        if(grid[i][j] == 2 && visited.Count == visitCount){
            count++;
            return;
        }
        
        visited.Add(loc);
        
        this.Traverse(grid, i+1, j, visited, rows, cols);
        this.Traverse(grid, i, j+1, visited, rows, cols);
        this.Traverse(grid, i-1, j, visited, rows, cols);
        this.Traverse(grid, i, j-1, visited, rows, cols);
        
        visited.Remove(loc);
    }
}
```
