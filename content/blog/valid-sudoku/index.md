---
title: Valid Sudoku
date: "2020-02-14"
type: problem-solving
description: Valid Sudoku
tags: csharp
---

Note: This problem was taken from LeetCode - [Valid Sudoku](https://leetcode.com/problems/valid-sudoku/)

### Naive Approach

Loop through each row and check if the number is repeated using a `HashSet`. Clear the `HashSet and repeat the same on the next row. When looping through each row, check if the HashSet already contains the number, if yes it's not valid sudoku.

Repeat the same process on each column as well as each `3x3` rows. This return the required result. If it passes all three of these validations, then it's valid sudoku.

```csharp
public bool IsValidSudoku(char[][] board) {
    HashSet<int> tempSet = new HashSet<int>();
    
    for(int i = 0; i < 9; i++){
        tempSet.Clear();
        for(int j = 0; j < 9; j++){
            if(board[i][j] != '.' && tempSet.Contains(board[i][j])){
                return false;
            }
            tempSet.Add(board[i][j]);
        }
    }
    
    for(int i = 0; i < 9; i++){
        tempSet.Clear();
        for(int j = 0; j < 9; j++){
            if(board[j][i] != '.' && tempSet.Contains(board[j][i])){
                return false;
            }
            tempSet.Add(board[j][i]);
        }
    }
    
    for(int i = 0; i < 3; i++){
        for(int j = 0; j < 3; j++){
            tempSet.Clear();
            for(int a = 0; a < 3; a++){
                for(int b = 0; b < 3; b++){
                    if(board[(3 * i) + a][(3 * j) + b] != '.' && tempSet.Contains(board[(3 * i) + a][(3 * j) + b])){
                        return false;
                    }
                    tempSet.Add(board[(3 * i) + a][(3 * j) + b]);
                }
            }
        }
    }
    
    return true;
}
```

In the above solution, we are using a single HashSet and validating it 3 times. We could improve the time taken by using 3 HashSets and validating all at once.
