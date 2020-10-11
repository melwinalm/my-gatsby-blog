---
title: Remove Duplicate Letters
date: "2020-10-11"
type: problem-solving
description: Remove Duplicate Letters
tags: csharp
---

Note: This problem was taken from LeetCode - [Remove Duplicate Letters](https://leetcode.com/problems/remove-duplicate-letters/)

### Naive Solution

```csharp
public string RemoveDuplicateLetters(string s) {
	if(s.Length == 0){
		return "";
	}
	
	int[] count = new int[26];
	
	for(int i = 0; i < s.Length; i++){
		count[s[i] - 'a']++;
	}
	
	StringBuilder sb = new StringBuilder();
	HashSet<char> set = new HashSet<char>();
	
	for(int i = 0; i < s.Length; i++){
		count[s[i] - 'a']--;
		
		if(set.Contains(s[i])){
			continue;
		}
		
		while(sb.Length > 0 && sb[sb.Length - 1] > s[i] && count[sb[sb.Length - 1] - 'a'] > 0){
			set.Remove(sb[sb.Length - 1]);
			sb.Length--;
		}
		
		set.Add(s[i]);
		sb.Append(s[i]);
	}
	
	return sb.ToString();
}
```
