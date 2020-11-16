---
title: Determine if Two Strings Are Close
date: "2020-11-16"
type: problem-solving
description: Determine if Two Strings Are Close
tags: csharp
---

Note: This problem was taken from LeetCode - [Determine if Two Strings Are Close](https://leetcode.com/problems/determine-if-two-strings-are-close/)

### Using Frequency Count

```csharp
public bool CloseStrings(string word1, string word2) {
	if(word1.Length != word2.Length){
		return false;
	}
	
	int[] word1Count = new int[26];
	int[] word2Count = new int[26];
	
	for(int i = 0; i < word1.Length; i++){
		word1Count[word1[i] - 'a']++;
		word2Count[word2[i] - 'a']++;
	}
	
	for(int i = 0; i < 26; i++){
		if((word1Count[i] > 0 && word2Count[i] == 0) || (word1Count[i] == 0 && word2Count[i] > 0)){
			return false;
		}
	}
	
	Array.Sort(word1Count);
	Array.Sort(word2Count);
	
	for(int i = 0; i < 26; i++){
		if(word1Count[i] != word2Count[i]){
			return false;
		}
	}
	
	return true;
}
```
