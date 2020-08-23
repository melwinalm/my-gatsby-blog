---
title: Thousand Separator
date: "2020-08-23"
type: problem-solving
description: Thousand Separator
tags: csharp
---

Note: This problem was taken from LeetCode - [Thousand Separator](https://leetcode.com/problems/thousand-separator/)

### Naive Approach

```csharp
public string ThousandSeparator(int n) {        
	string output = "";
	
	while(n > 999){
		output = "." + (n%1000).ToString("D3") + output;
		n /= 1000;
	}

	return n.ToString() + output;
}
```
