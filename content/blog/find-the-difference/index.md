---
title: Find the Difference
date: "2020-09-24"
type: problem-solving
description: Find the Difference
tags: csharp
---

Note: This problem was taken from LeetCode - [Find the Difference](https://leetcode.com/problems/find-the-difference/)

### Using Dictionary

```csharp
public char FindTheDifference(string s, string t) {
	Dictionary<char,int> map = new Dictionary<char,int>();
	
	foreach(char c in s){
		if(!map.ContainsKey(c)){
			map[c] = 0;
		}
		
		map[c] += 1;
	}
	
	foreach(char c in t){
		if(!map.ContainsKey(c) || map[c] == 0){
			return c;
		}
		map[c] -= 1;
	}
	
	return ' ';
}
```

### Using Bit Manipulation

XOR all the characters from both the strings. The repeated characters will cancel out, leaving behind the result.

```csharp
public char FindTheDifference(string s, string t) {
	int res = 0;
	
	foreach(char c in s){
		res ^= c;
	}
	
	foreach(char c in t){
		res ^= c;
	}
	
	return Convert.ToChar(res);
}
```
