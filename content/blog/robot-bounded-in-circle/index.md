---
title: Robot Bounded In Circle
date: "2020-09-17"
type: problem-solving
description: Robot Bounded In Circle
tags: csharp
---

Note: This problem was taken from LeetCode - [Robot Bounded In Circle](https://leetcode.com/problems/robot-bounded-in-circle/)

### Naive Approach

```csharp
public bool IsRobotBounded(string instructions) {
	int x = 0;
	int y = 0;
	int i = 0;
	int[,] dirs = new int[,]{{0, 1}, {1, 0}, {0, -1}, {-1, 0}};
	
	foreach(char c in instructions)
		if (c == 'R')
			i = (i + 1) % 4;
		else if (c == 'L')
			i = (i + 3) % 4;
		else {
			x += dirs[i,0];
			y += dirs[i,1];
		}
	return x == 0 && y == 0 || i > 0;
}
```
