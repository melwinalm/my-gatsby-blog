---
title: Valid Square
date: "2020-11-11"
type: problem-solving
description: Valid Square
tags: csharp
---

Note: This problem was taken from LeetCode - [Valid Square](https://leetcode.com/problems/valid-square/)

### Using HashSet

```csharp
public bool ValidSquare(int[] p1, int[] p2, int[] p3, int[] p4) {
	HashSet<int> set = new HashSet<int>();
	
	set.Add(this.Dist(p1, p2));
	set.Add(this.Dist(p1, p3));
	set.Add(this.Dist(p1, p4));
	set.Add(this.Dist(p2, p3));
	set.Add(this.Dist(p2, p4));
	set.Add(this.Dist(p3, p4));
	
	// there should be 4 equal sides and 2 equal diagonals
	return set.Count == 2 && !set.Contains(0);
}

public int Dist(int[] pt1, int[] pt2){
	return (int)Math.Pow(pt1[0] - pt2[0], 2) + (int)Math.Pow(pt1[1] - pt2[1], 2);
}
```
