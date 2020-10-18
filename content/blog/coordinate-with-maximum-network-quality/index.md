---
title: Coordinate With Maximum Network Quality
date: "2020-10-18"
type: problem-solving
description: Coordinate With Maximum Network Quality
tags: csharp
---

Note: This problem was taken from LeetCode - [Coordinate With Maximum Network Quality](https://leetcode.com/problems/coordinate-with-maximum-network-quality/)

### Brute Force Solution

```csharp
public int[] BestCoordinate(int[][] towers, int radius) {
	int N = towers.Length;
	
	int[] netQuality = new int[N];
	
	Dictionary<string, int> map = new Dictionary<string, int>();
	
	double rSquare = radius * radius;
	
	int maxSoFar = 0;
	
	for(int i = 0; i < N; i++){
		for(int j = 0; j < N; j++){
			double dist = Math.Pow(towers[i][0] - towers[j][0], 2) + Math.Pow(towers[i][1] - towers[j][1], 2);
			
			if(dist > rSquare){
				continue;
			}
			
			netQuality[i] += (int)Math.Floor(towers[j][2] / (1 + Math.Sqrt(dist)));
		}
		
		maxSoFar = Math.Max(maxSoFar, netQuality[i]);
	}
	
	int[] result = new int[]{Int32.MaxValue, Int32.MaxValue};
	
	for(int i = 0; i < N; i++){
		if(maxSoFar == netQuality[i]){
			
			if(towers[i][0] < result[0]){
				result[0] = towers[i][0];
				result[1] = towers[i][1];
			}
			else if(towers[i][0] == result[0]){
				if(towers[i][1] < result[1]){
					result[0] = towers[i][0];
					result[1] = towers[i][1];
				}
			}
			
		}
	}
	
	return result;        
}
```
