---
title: Split a String in Balanced Strings
date: "2020-08-25"
type: problem-solving
description: Split a String in Balanced Strings
tags: csharp
---

Note: This problem was taken from LeetCode - [Split a String in Balanced Strings](https://leetcode.com/problems/split-a-string-in-balanced-strings/)

### Greedy Approach

```csharp
public int BalancedStringSplit(string s) {
	int count = 0;
	
	int balance = 0;
	
	foreach(char c in s){
		if(c == 'R'){
			balance++;
		}
		else if(c == 'L'){
			balance--;
		}
		
		if(balance == 0){
			count++;
		}
		
	}
	
	return count;
}
```
