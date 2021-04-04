---
title: Longest Valid Parentheses
date: "2021-04-04"
type: problem-solving
description: Longest Valid Parentheses
tags: csharp
---

Note: This problem was taken from LeetCode - [Longest Valid Parentheses](https://leetcode.com/problems/longest-valid-parentheses/)

### Using Stack

```csharp
public int LongestValidParentheses(string s) {
	Stack<int> stack = new Stack<int>();
	stack.Push(-1);
	
	int result = 0;
	
	for(int i = 0; i < s.Length; i++){
		if(s[i] == '('){
			stack.Push(i);
		}
		else{
			stack.Pop();
			if(stack.Count == 0){
				stack.Push(i);
			}
			else{
				result = Math.Max(result, i - stack.Peek());
			}
		}
	}
	
	return result;
}
```
