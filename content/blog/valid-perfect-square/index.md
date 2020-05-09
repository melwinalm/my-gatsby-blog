---
title: Valid Perfect Square
date: "2020-05-09"
type: problem-solving
description: Valid Perfect Square
tags: csharp
---

Note: This problem was taken from LeetCode - [Valid Perfect Square](https://leetcode.com/problems/valid-perfect-square/)

### Using Summataion

Sum of n odd numbers is given by n^2. Below solution uses this method

```csharp
public bool IsPerfectSquare(int num) {
	int i = 1;
	
	while(num > 0){
		num -= i;
		i += 2;
	}
	
	return num == 0;
}
```
