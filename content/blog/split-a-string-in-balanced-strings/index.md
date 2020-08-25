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
	
	int lCount = 0;
	int rCount = 0;
	
	for(int i = 0; i < s.Length; i++){
		if(s[i] == 'L'){
			lCount += 1;
		}
		else{
			rCount += 1;
		}
		
		
		if(lCount == rCount){
			count++;
			lCount = 0;
			rCount = 0;
		}
	}
	
	return count;
}
```
