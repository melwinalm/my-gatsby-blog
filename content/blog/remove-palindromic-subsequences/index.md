---
title: Remove Palindromic Subsequences
date: "2021-03-08"
type: problem-solving
description: Remove Palindromic Subsequences
tags: csharp
---

Note: This problem was taken from LeetCode - [Remove Palindromic Subsequences](https://leetcode.com/problems/remove-palindromic-subsequences/)

### Naive Solution

case 1: Length of the string is 0 then the result is 0
case 2: Given string is palindrome then the result is 1
case 3: In all other cases the result is 2

```csharp
public int RemovePalindromeSub(string s) {
	if(s.Length == 0){
		return 0;
	}
	
	int i = 0;
	int j = s.Length - 1;
	
	while(i < j){
		if(s[i] == s[j]){
			i++;
			j--;
		}
		else{
			return 2;
		}
	}
	
	return 1;
}
```
