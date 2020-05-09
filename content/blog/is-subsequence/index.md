---
title: Is Subsequence
date: "2020-05-09"
type: problem-solving
description: Is Subsequence
tags: csharp
---

Note: This problem was taken from LeetCode - [Is Subsequence](https://leetcode.com/problems/is-subsequence/)

### Two-Pointer Approach

```csharp
public bool IsSubsequence(string s, string t) {
	int sIndex = 0;
	int tIndex = 0;
	while(sIndex < s.Length && tIndex < t.Length){
		if(s[sIndex] == t[tIndex]){
			sIndex++;
			tIndex++;
		}
		else{
			tIndex++;                
		}
	}
	
	if(sIndex == s.Length){
		return true;
	}
	
	return false;
}
```
