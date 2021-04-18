---
title: Check if the Sentence Is Pangram
date: "2021-04-18"
type: problem-solving
description: Check if the Sentence Is Pangram
tags: csharp
---

Note: This problem was taken from LeetCode - [Check if the Sentence Is Pangram](https://leetcode.com/problems/check-if-the-sentence-is-pangram/)

### Using HashSet

```csharp
public bool CheckIfPangram(string sentence) {
	HashSet<char> set = new HashSet<char>();
	
	foreach(char c in sentence){
		set.Add(c);            
	}
	
	return set.Count == 26;
}
```
