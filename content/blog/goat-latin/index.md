---
title: Goat Latin
date: "2020-08-19"
type: problem-solving
description: Goat Latin
tags: csharp
---

Note: This problem was taken from LeetCode - [Goat Latin](https://leetcode.com/problems/goat-latin/)

### Naive Approach

```csharp
public string ToGoatLatin(string S) {
	string[] words = S.Split(" ");
	
	string appendWord = "a";
	
	for(int i = 0; i < words.Length; i++){
		if(this.IsVowel(words[i])){
			words[i] += "ma";
		}
		else{
			words[i] = (words[i] + words[i][0] + "ma").Substring(1);
		}
		
		words[i] += appendWord;
		appendWord += "a";
	}
	
	return string.Join(" ", words);
}

private bool IsVowel(string word){
	if(word.Length == 0){
		return false;
	}
	
	char fChar = char.ToLower(word[0]);
	
	if(fChar == 'a' || fChar == 'e' || fChar == 'i' || fChar == 'o' || fChar == 'u'){
		return true;
	}
	
	return false;
}
```
