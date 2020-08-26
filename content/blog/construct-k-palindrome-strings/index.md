---
title: Construct K Palindrome Strings
date: "2020-08-26"
type: problem-solving
description: Construct K Palindrome Strings
tags: csharp
---

Note: This problem was taken from LeetCode - [Construct K Palindrome Strings](https://leetcode.com/problems/construct-k-palindrome-strings/)

### Greedy Approach

```csharp
public bool CanConstruct(string s, int k) {
	int maxSplits = s.Length;

	// If k is greater than the length of the string then we cannot divide since the question explicitly mentions that there cannot be any palindromes with length 0
	if(k > maxSplits){
		return false;
	}
	
	Dictionary<char,int> map = new Dictionary<char,int>();
	
	foreach(char c in s){
		if(!map.ContainsKey(c)){
			map[c] = 0;
		}
		map[c] += 1;
	}
	
	// This variable holds the minimum number of splits that will have to be made to construct the palindromic strings.
	// If k is greater than minSplits then we can construct else we cannot.
	int minSplits = 0;
	
	// minSplits basically calculates the number of characters which have odd frequency count, since odd numbered characters have to be a separate palindrome
	foreach(var item in map){
		if(item.Value % 2 == 1){
			minSplits++;
		}
	}
	
	// If the minspits is 0 then there will be atleat one palindrome with all characters
	if(minSplits == 0){
		minSplits = 1;
	}
	
	if(k >= minSplits){
		return true;
	}
	else{
		return false;
	}
}
```
