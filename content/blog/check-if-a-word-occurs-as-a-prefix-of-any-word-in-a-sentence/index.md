---
title: Check If a Word Occurs As a Prefix of Any Word in a Sentence
date: "2020-05-24"
type: problem-solving
description: Check If a Word Occurs As a Prefix of Any Word in a Sentence
tags: csharp
---

Note: This problem was taken from LeetCode - [Check If a Word Occurs As a Prefix of Any Word in a Sentence](https://leetcode.com/problems/check-if-a-word-occurs-as-a-prefix-of-any-word-in-a-sentence/)

### Using Linear Scan

```csharp
public int IsPrefixOfWord(string sentence, string searchWord) {
	string[] words = sentence.Split(' ');
	
	for(int i = 0; i < words.Length; i++){
		if(this.CustomContains(words[i], searchWord)){
			return i + 1; 
		}
	}
	
	return -1;        
}

public bool CustomContains(string parent, string child){
	if(child.Length > parent.Length){
		return false;
	}
	
	for(int i = 0; i < child.Length; i++){
		if(parent[i] != child[i]){
			return false;
		}
	}
	
	return true;
}
```
