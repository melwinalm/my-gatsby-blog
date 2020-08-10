---
title: Excel Sheet Column Number
date: "2020-08-10"
type: problem-solving
description: Excel Sheet Column Number
tags: csharp
---

Note: This problem was taken from LeetCode - [Excel Sheet Column Number](https://leetcode.com/problems/excel-sheet-column-number/)

```csharp
public int TitleToNumber(string s) {
	int power = 1;
	int output = 0;
	
	for(int i = s.Length-1; i >= 0; i--){
		int value = s[i] - 'A' + 1;
		
		output += (value * power);
		power *= 26;
	}
	
	return output;
}
```
