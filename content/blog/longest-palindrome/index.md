---
title: Longest Palindrome
date: "2020-08-14"
type: problem-solving
description: Longest Palindrome
tags: csharp
---

Note: This problem was taken from LeetCode - [Longest Palindrome](https://leetcode.com/problems/longest-palindrome/)

### Using Dictionary

```csharp
public int LongestPalindrome(string s) {
	Dictionary<char, int> map = new Dictionary<char, int>();

	foreach(char c in s){
		if(!map.ContainsKey(c)){
			map[c] = 0;
		}

		map[c]++;
	}

	int sumOddCount = 0;
	int sumEvenCount = 0;
	bool oddFound = false;

	foreach(var item in map){
		if(item.Value % 2 == 0){
			sumEvenCount += item.Value;
		}
		else{
			sumOddCount += item.Value - 1;
			oddFound = true;
		}
	}

	if(oddFound){
		return sumOddCount + sumEvenCount + 1;
	}
	else{
		return sumEvenCount;
	}
}
```
