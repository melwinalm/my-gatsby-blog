---
title: First Unique Character in a String
date: "2020-05-05"
type: problem-solving
description: First Unique Character in a String
tags: csharp
---

Note: This problem was taken from LeetCode - [First Unique Character in a String](https://leetcode.com/problems/first-unique-character-in-a-string/)

### Using Dictionary

```csharp
public int FirstUniqChar(string s) {
	Dictionary<char, int> output = new Dictionary<char, int>();
	
	for(int i = 0; i < s.Length; i++){
		if(output.ContainsKey(s[i])){
			output[s[i]] = -1;
		}
		else{
			output[s[i]] = i;
		}
	}
	
	foreach(var item in output){
		if(item.Value != -1){
			return item.Value;
		}
	}
	
	return -1;
}
```
