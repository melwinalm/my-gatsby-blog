---
title: Consecutive Characters
date: "2020-05-16"
type: problem-solving
description: Consecutive Characters
tags: csharp
---

Note: This problem was taken from LeetCode - [Consecutive Characters](https://leetcode.com/problems/consecutive-characters/)

### Linear Scan

```csharp
public int MaxPower(string s) {
	if(s.Length < 2){
		return s.Length;
	}
	
	int maxCount = 1;
	int currCount = 1;
	for(int i = 1; i < s.Length; i++){
		if(s[i] == s[i-1]){
			currCount++;
		}
		else{
			maxCount = Math.Max(currCount, maxCount);
			currCount = 1;
		}
	}
	maxCount = Math.Max(currCount, maxCount);
	
	return maxCount;
}
```
