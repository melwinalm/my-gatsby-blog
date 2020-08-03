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
	int start = 0;
	int end = s.Length - 1;
	
	while(start < end){
		if(!char.IsLetterOrDigit(s[start])){
			start++;
			continue;
		}
		
		if(!char.IsLetterOrDigit(s[end])){
			end--;
			continue;
		}
		
		if(char.ToLower(s[start]) != char.ToLower(s[end])){
			return false;
		}
		start++;
		end--;
	}
	
	return true;
}
```
