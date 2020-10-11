---
title: Maximum Nesting Depth of the Parentheses
date: "2020-10-11"
type: problem-solving
description: Maximum Nesting Depth of the Parentheses
tags: csharp
---

Note: This problem was taken from LeetCode - [Maximum Nesting Depth of the Parentheses](https://leetcode.com/problems/maximum-nesting-depth-of-the-parentheses/)

### Naive Solution

```csharp
public int MaxDepth(string s) {
	int maxSoFar = 0;
	int curr = 0;
	
	foreach(char c in s){
		if(c == '('){
			curr++;
		}
		else if(c == ')'){
			curr--;
		}
		maxSoFar = Math.Max(curr, maxSoFar);
	}
	
	return maxSoFar;
}
```
