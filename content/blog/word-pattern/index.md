---
title: Word Pattern
date: "2020-09-07"
type: problem-solving
description: Word Pattern
tags: csharp
---

Note: This problem was taken from LeetCode - [Word Pattern](https://leetcode.com/problems/word-pattern/)

### Using Two HashSets

```minCost += (group sum of repeated characters) - (max number in that group)```

```csharp
public bool WordPattern(string pattern, string str) {
	Dictionary<char,string> c2str = new Dictionary<char, string>();
	Dictionary<string,char> str2c = new Dictionary<string,char>();
	string[] words = str.Split(" ");
	
	if(words.Length != pattern.Length){
		return false;
	}
	
	for(int i = 0; i < pattern.Length; i++){
		if(c2str.ContainsKey(pattern[i]) && str2c.ContainsKey(words[i])){
			if(c2str[pattern[i]] != words[i] || str2c[words[i]] != pattern[i]){
				return false;
			}
		}
		else if((c2str.ContainsKey(pattern[i]) && !str2c.ContainsKey(words[i])) || (!c2str.ContainsKey(pattern[i]) && str2c.ContainsKey(words[i]))){
			return false;
		}
		else{
			c2str[pattern[i]] = words[i];   
			str2c[words[i]] = pattern[i];
		}
	}
	
	return true;
}
```
