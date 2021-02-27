---
title: Score of Parentheses
date: "2021-02-27"
type: problem-solving
description: Score of Parentheses
tags: csharp
---

Note: This problem was taken from LeetCode - [Score of Parentheses](https://leetcode.com/problems/score-of-parentheses/)

### Using Stack

```csharp
public int ScoreOfParentheses(string S) {
	Stack<int> stack = new Stack<int>();
	int current = 0;
	
	foreach(char c in S){
		if(c == '('){
			stack.Push(current);
			current = 0;
		}
		else{
			current = stack.Pop() + Math.Max(current * 2, 1);
		}
	}
	
	return current;
} 
```
