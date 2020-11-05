---
title: Champagne Tower
date: "2020-11-05"
type: problem-solving
description: Champagne Tower
tags: csharp
---

Note: This problem was taken from LeetCode - [Champagne Tower](https://leetcode.com/problems/champagne-tower/)

### Using Simulation

```csharp
public double ChampagneTower(int poured, int query_row, int query_glass) {
	double[,] output = new double[102,102];
	output[0,0] = (double)poured;
	
	for(int r = 0; r <= query_row; r++){
		for(int c = 0; c <= r; c++){
			double q = (output[r,c] - 1.0) / 2.0;
			
			if(q > 0){
				output[r+1,c] += q;
				output[r+1,c+1] += q;
			}
		}
	}
	
	return Math.Min(1, output[query_row,query_glass]);
}
```
