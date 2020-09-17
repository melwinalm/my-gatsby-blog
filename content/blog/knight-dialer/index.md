---
title: Knight Dialer
date: "2020-09-17"
type: problem-solving
description: Knight Dialer
tags: csharp
---

Note: This problem was taken from LeetCode - [Knight Dialer](https://leetcode.com/problems/knight-dialer/)

### Using Depth First Search (Time Limit Exceeded Error)

```csharp
public int KnightDialer(int n) {
	int[] moveX = new int[] {1, 2, 2, 1, -1, -2, -2, -1};
	int[] moveY = new int[] {2, 1, -1, -2, -2, -1, 1, 2};
	
	int[,] dialer = new int[,]{{1,2,3}, {4,5,6}, {7,8,9}, {-1, 0,-1}};
	
	int count = 0;
	
	for(int i = 0; i < 4; i++){
		for(int j = 0; j < 3; j++){
			if(dialer[i,j] == -1){
				continue;
			}
			
			count += this.KD(i, j, n-1, moveX, moveY, dialer);
		}
	}
	
	return count;
}

public int KD(int i, int j, int remN, int[] moveX, int[] moveY, int[,] dialer){
	if(i < 0 || j < 0 || i >= 4 || j >= 3 || dialer[i,j] == -1){
		return 0;
	}
	
	if(remN == 0){
		return 1;
	}
	
	int count = 0;
	
	for(int a = 0; a < 8; a++){
		int newX = i + moveX[a];
		int newY = j + moveY[a];
		
		count += this.KD(newX, newY, remN-1, moveX, moveY, dialer);
	}
	
	return count;
}
```

### Using DP

TBD
