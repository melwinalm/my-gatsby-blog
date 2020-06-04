---
title: Reverse String
date: "2020-06-04"
type: problem-solving
description: Reverse String
tags: csharp
---

Note: This problem was taken from LeetCode - [Reverse String](https://leetcode.com/problems/reverse-string/)

### Using Two Pointer Technique

```csharp
public void ReverseString(char[] s) {
	int startIndex = 0;
	int endIndex = s.Length - 1;
	
	while(startIndex < endIndex){
		char temp = s[startIndex];
		s[startIndex] = s[endIndex];
		s[endIndex] = temp;
		startIndex++;
		endIndex--;
	}
}
```
