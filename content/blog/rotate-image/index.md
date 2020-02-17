---
title: Rotate Image
date: "2020-02-3"
type: problem-solving
description: Rotate Image
tags: csharp
---

Note: This problem was taken from LeetCode - [Rotate Image](https://leetcode.com/problems/rotate-image/)

### Transpose and Rotate Approach

In this approach find the transpose of the matrix first and then mirror image the matrix vertically.

```csharp
public void Rotate(int[][] matrix) {
    int N = matrix.Length;

    // Transpose the matrix
    for(int i = 0; i < N; i++){
        for(int j = i; j < N; j++){
            int temp = matrix[i][j];
            matrix[i][j] = matrix[j][i];
            matrix[j][i] = temp;
        }
    }
    
    // Swap the matrix vertically
    for(int i = 0; i < N; i++){
        for(int j = 0; j < N/2; j++){
            int temp = matrix[i][j];
            matrix[i][j] = matrix[i][N - j - 1];
            matrix[i][N - j - 1] = temp;
        }
    }
}
```

### In-Place Rotation Method

Here we start swapping elements starting from the outer most layer. Keep doing this till the center, to get the rotated image.

```csharp
public void Rotate(int[][] matrix) {
    int N = matrix.Length;

    for(int i = 0; i < N / 2; i++){
        for(int j = i; j < N - i - 1; j++){
            int temp = matrix[N-j-1][i];
            matrix[N-j-1][i] = matrix[N-i-1][N-j-1];
            matrix[N-i-1][N-j-1] = matrix[j][N-i-1]; 
            matrix[j][N-i-1] = matrix[i][j];
            matrix[i][j] = temp;
        }
    }
}
```
