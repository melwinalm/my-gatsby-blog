---
title: Repeated Substring Pattern
date: "2020-09-03"
type: problem-solving
description: Repeated Substring Pattern
tags: csharp
---

Note: This problem was taken from LeetCode - [Repeated Substring Pattern](https://leetcode.com/problems/repeated-substring-pattern/)

### Using Window Approach

```csharp
public bool RepeatedSubstringPattern(string s) {
	if(s.Length == 0){
		return true;
	}
	int winSize = 1;
	
	while(winSize <= (s.Length/2)){
		
		// Checking if this window size can fit in the given string. If not, then skip checking for that window size.
		if(s.Length % winSize != 0){
			winSize++;
			continue;
		}
		
		int windows = s.Length / winSize;
		
		bool flag = true;
		
		for(int i = 1; i < windows; i++){
			if(s.Substring(0, winSize) != s.Substring(i*winSize, winSize)){
				flag = false;
				break;
			}
		}
		
		if(flag == true){
			return true;
		}
		
		winSize++;
	}
	
	return false;
}
```

### Approach 2

```csharp
public bool RepeatedSubstringPattern(string s) {
	string newStr = s + s;
	return newStr.Substring(1, newStr.Length-2).Contains(s);
}
```
