---
title: Word Break
date: "2020-09-29"
type: problem-solving
description: Word Break
tags: csharp
---

Note: This problem was taken from LeetCode - [Word Break](https://leetcode.com/problems/word-break/)

### Brute Force (N^2 time complexity)

```csharp
public bool WordBreak(string s, IList<string> wordDict) {
	HashSet<string> dict = new HashSet<string>(wordDict);
	
	return DFS(s, dict);
}

public bool DFS(string s, HashSet<string> dict){
	int len = s.Length;
	
	if(len == 0){
		return true;
	}
	
	for(int i = 1; i <= len; i++){
		if(dict.Contains(s.Substring(0, i)) && this.DFS(s.Substring(i), dict)){
			return true;
		}
	}        
	
	return false;
}
```

### Using Dynamic Programming

```csharp
public bool WordBreak(string s, IList<string> wordDict) {
	HashSet<string> set = new HashSet<string>(wordDict);
	
	bool[] memo = new bool[s.Length + 1];
	
	memo[0] = true;
	
	for(int i = 1; i <= s.Length; i++){
		for(int j = 0; j < i; j++){
			if(memo[j] && set.Contains(s.Substring(j,i-j))){
				memo[i] = true;
				break;
			}
		}
	}
	
	return memo[s.Length];
}
```
