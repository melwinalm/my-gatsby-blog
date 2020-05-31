---
title: Check If a String Contains All Binary Codes of Size K
date: "2020-05-30"
type: problem-solving
description: Check If a String Contains All Binary Codes of Size K
tags: csharp
---

Note: This problem was taken from LeetCode - [Check If a String Contains All Binary Codes of Size K](https://leetcode.com/problems/check-if-a-string-contains-all-binary-codes-of-size-k/)

### Using DFS

```csharp
public bool HasAllCodes(string s, int k) {
	HashSet<string> codes = new HashSet<string>();

	int maxCombos = (int)Math.Pow(2, k);
	
	for(int i = 0; i <= s.Length - k; i++){
		codes.Add(s.Substring(i, k));            
	}
	
	return maxCombos == codes.Count;
}
```
