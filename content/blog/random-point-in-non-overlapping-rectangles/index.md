---
title: Random Point in Non-overlapping Rectangles
date: "2020-08-22"
type: problem-solving
description: Random Point in Non-overlapping Rectangles
tags: csharp
---

Note: This problem was taken from LeetCode - [Random Point in Non-overlapping Rectangles](https://leetcode.com/problems/random-point-in-non-overlapping-rectangles/)

```csharp
int[][] rectangles;
SortedDictionary<int, int> map;
Random rand;
int area;

public Solution(int[][] rects) {
	rand = new Random();
	map = new SortedDictionary<int,int>();
	
	rectangles = rects;
	
	for(int i = 0 ; i < rectangles.Length; i++){
		area += (rectangles[i][2] - rectangles[i][0] + 1) * (rectangles[i][3] - rectangles[i][1] + 1);
		map.Add(area, i);
	}
}

public int[] Pick() {
	int randNum = rand.Next(area) + 1;
	
	int rectIndex = map.First(x => x.Key >= randNum).Value;
	
	int x = rand.Next(rectangles[rectIndex][0], rectangles[rectIndex][2] + 1);
	int y = rand.Next(rectangles[rectIndex][1], rectangles[rectIndex][3] + 1);
	
	return new int[]{x,y};
}
```
