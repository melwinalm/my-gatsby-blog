---
title: Subrectangle Queries
date: "2020-06-15"
type: problem-solving
description: Subrectangle Queries
tags: csharp
---

Note: This problem was taken from LeetCode - [Subrectangle Queries](https://leetcode.com/problems/subrectangle-queries/)

### Basic  Solution

```csharp
public class SubrectangleQueries {
    int rows;
    int cols;
    int[,] matrix;

    public SubrectangleQueries(int[][] rectangle) {
        rows = rectangle.Length;
        if(rows == 0){
            cols = 0;
            matrix = new int[rows, cols];
            return;
        }
        
        cols = rectangle[0].Length;
        matrix = new int[rows,cols];
        
        for(int i = 0; i < rows; i++){
            for(int j = 0; j < cols; j++){
                matrix[i,j] = rectangle[i][j];
            }
        }
    }
    
    public void UpdateSubrectangle(int row1, int col1, int row2, int col2, int newValue) {
        for(int i = row1; i <= row2; i++){
            for(int j = col1; j <= col2; j++){
                matrix[i,j] = newValue;
            }
        }
    }
    
    public int GetValue(int row, int col) {
        if(row >= rows || col >= cols || row < 0 || col < 0){
            return 0;
        }
        
        return matrix[row,  col];
    }
}
```
