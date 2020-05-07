---
title: Valid Palindrome
date: "2020-05-07"
type: problem-solving
description: Valid Palindrome
tags: csharp
---

Note: This problem was taken from LeetCode - [Valid Palindrome](https://leetcode.com/problems/valid-palindrome/)

### Using Two Pointer Technique
```csharp
public bool IsPalindrome(string s) {
	int sIndex = 0;
	int eIndex = s.Length - 1;
	
	while(sIndex < eIndex){
		while(sIndex < eIndex && !Char.IsLetterOrDigit(s[sIndex])){
			sIndex++;
		}
		
		while(sIndex < eIndex && !Char.IsLetterOrDigit(s[eIndex])){
			eIndex--;
		}
		
		if(sIndex < eIndex){
			if(Char.ToLower(s[sIndex]) != Char.ToLower(s[eIndex])){
				return false;
			}
		}
		sIndex++;
		eIndex--;
	}
	
	return true;
}
```
