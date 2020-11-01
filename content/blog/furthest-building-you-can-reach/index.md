---
title: Furthest Building You Can Reach
date: "2020-11-01"
type: problem-solving
description: Furthest Building You Can Reach
tags: csharp
---

Note: This problem was taken from LeetCode - [Furthest Building You Can Reach](https://leetcode.com/problems/furthest-building-you-can-reach/)

### Using Top Down Approach (Time Limit Exceeded Error)

```csharp
public int FurthestBuilding(int[] heights, int bricks, int ladders) {
	if(heights.Length == 1){
		return 1;
	}
	
	return this.Furthest(heights, 1, bricks, ladders);
}

public int Furthest(int[] heights, int currIndex, int remBricks, int remLadders){
	if(remBricks < 0 || remLadders < 0){
		return currIndex-2;
	}
	
	if(currIndex >= heights.Length){
		if(remBricks >= 0 && remLadders >= 0){
			return heights.Length - 1;
		}
		else{
			return 0;
		}
	}
	
	if(heights[currIndex] <= heights[currIndex - 1]){
		return this.Furthest(heights, currIndex+1, remBricks, remLadders);
	}
	else{
		return Math.Max(
			this.Furthest(heights, currIndex+1, remBricks - Math.Abs(heights[currIndex]-heights[currIndex-1]), remLadders),
			this.Furthest(heights, currIndex+1, remBricks, remLadders-1)
		);
	}
	
}
```

### Using Priority Queue

```csharp
public int FurthestBuilding(int[] heights, int bricks, int ladders)
{
	SortedSet<Tuple<int,int>> pq = new SortedSet<Tuple<int,int>>();
	
	for(int i = 0; i < heights.Length - 1; i++){
		int d = heights[i+1] - heights[i];
		
		if(d <= 0){
			continue;
		}
		
		pq.Add(new Tuple<int,int>(d, i));
		
		if(pq.Count > ladders){
			bricks -= pq.Min.Item1;
			pq.Remove(pq.Min);
		}
		
		if(bricks < 0){
			return i;
		}
		
	}
	
	return heights.Length - 1;
}
```
