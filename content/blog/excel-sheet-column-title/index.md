---
title: Excel Sheet Column Title
date: "2020-09-03"
type: problem-solving
description: Excel Sheet Column Title
tags: csharp
---

Note: This problem was taken from LeetCode - [Excel Sheet Column Title](https://leetcode.com/problems/excel-sheet-column-title/)

### Using Trie

```csharp
public string ConvertToTitle(int n) {
	string output = "";
	
	while(n > 0){
		n--;
		int val = n % 26;
		output = Convert.ToChar(65 + val) + output;
		n /= 26;
	}
	
	return output;
}
```
