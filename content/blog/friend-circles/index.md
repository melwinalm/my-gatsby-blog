---
title: Friend Circles
date: "2020-06-04"
type: problem-solving
description: Friend Circles
tags: csharp
---

Note: This problem was taken from LeetCode - [Friend Circles](https://leetcode.com/problems/friend-circles/)

### Using Depth First Search

```csharp
public int FindCircleNum(int[][] M) {
	int count = 0;        
	int N = M.Length;
	
	for(int i = 0; i < N; i++){
		for(int j = 0; j < N; j++){
			if(M[i][j] == 1){
				this.DFS(M, N, i, j);
				count++;
			}
		}
	}
	
	return count;
}

public void DFS(int[][] M, int N, int i, int j){
	if(M[i][j] == 0){
		return;
	}
	
	M[i][j] = 0;
	
	for(int a = 0; a < N; a++){
		if(M[a][j] == 1){
			this.DFS(M, N, a, j);
		}
		
		if(M[i][a] == 1){
			this.DFS(M, N, i, a);
		}
	}
} 
```
