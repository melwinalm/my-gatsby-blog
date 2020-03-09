---
title: Rotting Oranges
date: "2020-03-09"
type: problem-solving
description: Rotting Oranges
tags: csharp
---

Note: This problem was taken from LeetCode - [Rotting Oranges](https://leetcode.com/problems/rotting-oranges/)

### Breadth-First Search Approach

```csharp
public int OrangesRotting(int[][] grid) {
    int R = grid.Length;
    int C = grid[0].Length;
    
    Queue<int> bfsQueue = new Queue<int>();
    
    int depth = 0;
    
    // Find all the rotten oranges and add them to the queue.
    for(int r = 0; r < R; r++){
        for(int c = 0; c < C; c++){
            if(grid[r][c] == 2){
                int loc = (r * C) + c;
                bfsQueue.Enqueue(loc);
            } 
        }
    }
    
    // These are the surrounding coordinates of a given coordinate
    int[] surrR = new int[] {-1, 0, 1, 0};
    int[] surrC = new int[] {0, -1, 0, 1};
    
    while(bfsQueue.Count != 0){
        int count = bfsQueue.Count;
        
        for(int k = 0; k < count; k++){
            int loc = bfsQueue.Dequeue();
        
            int r = loc / C;
            int c = loc % C;
            
            // Check all the four surroundings for any fresh oranges and add them to the queue
            for(int i = 0; i < 4; i++){
                int row = r + surrR[i];
                int col = c + surrC[i];
                
                if(row >= 0 && row < R && col >= 0 && col < C && grid[row][col] == 1){
                    grid[row][col] = 2;
                    int loc2 = (row * C) + col;
                    bfsQueue.Enqueue(loc2);
                }
            }
        }
        
        // If queue is empty then are no more fresh oranges hence don't increase the depth.
        if(bfsQueue.Count != 0){
            depth++;
        }
    }
    
    // Check if there are any oranges which are fresh, if yes then return -1.
    for(int i = 0; i < R; i++){
        for(int j = 0; j < C; j++){
            if(grid[i][j] == 1){
                return -1;
            }
        }
    }
    
    return depth;
}
```

This has a time and space complexity of O(N).
