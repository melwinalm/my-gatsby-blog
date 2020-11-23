---
title: Smallest String With A Given Numeric Value
date: "2020-11-23"
type: problem-solving
description: Smallest String With A Given Numeric Value
tags: csharp
---

Note: This problem was taken from LeetCode - [Smallest String With A Given Numeric Value](https://leetcode.com/problems/smallest-string-with-a-given-numeric-value/)

### Greedy Approach

```csharp
public string GetSmallestString(int n, int k) {
	char[] output = new char[n];
	Array.Fill(output, 'a');
	k -= n;
	
	int i = n - 1;
	
	while(k > 0){
		int newChar = Math.Min(k, 25);
		output[i] = Convert.ToChar(97 + newChar);
		k -= newChar;
		i--;
	}
	
	return new string(output);
}
```
