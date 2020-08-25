---
title: Minimum Add to Make Parentheses Valid
date: "2020-08-25"
type: problem-solving
description: Minimum Add to Make Parentheses Valid
tags: csharp
---

Note: This problem was taken from LeetCode - [Minimum Add to Make Parentheses Valid](https://leetcode.com/problems/minimum-add-to-make-parentheses-valid/)

### Greedy Approach (O(n) space complexity)

```csharp
public int MinAddToMakeValid(string S) {
	if(S.Length == 0){
		return 0;
	}
	
	Stack<char> st = new Stack<char>();
	
	int i = 1;
	st.Push(S[0]);
	
	while(i < S.Length){
		if(st.Count == 0){
			st.Push(S[i]);                
		}
		else if(st.Peek() == '(' && S[i] == ')'){
			st.Pop();
		}
		else{
			st.Push(S[i]);                
		}
		
		i++;
	}
	
	return st.Count;
}
```

### Greedy Approach (O(1) space complexity)

```csharp
public int MinAddToMakeValid(string S) {
	int openCount = 0;
	int closeCount = 0;
	
	foreach(char c in S){
		if(c == '('){
			openCount++;
		}
		else if(openCount > 0){
			openCount--;
		}
		else{
			closeCount++;
		}
	}
	
	return openCount + closeCount;
}
```
