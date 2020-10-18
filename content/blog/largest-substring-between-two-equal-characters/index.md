---
title: Largest Substring Between Two Equal Characters
date: "2020-10-18"
type: problem-solving
description: Largest Substring Between Two Equal Characters
tags: csharp
---

Note: This problem was taken from LeetCode - [Largest Substring Between Two Equal Characters](https://leetcode.com/problems/largest-substring-between-two-equal-characters/)

### Naive Solution - Pre-Computated(Time Limit Exceeded Error)

```csharp
public int MaxLengthBetweenEqualCharacters(string s) {
	int[] first = new int[26];
	int[] last = new int[26];
	
	Array.Fill(first, -1);
	Array.Fill(last, -1);
	
	for(int i = 0; i < s.Length; i++){
		int val = s[i] - 'a';
		
		if(first[val] == -1){
			first[val] = i;
		}
		
		last[val] = i;
	}
	
	int maxSoFar = -1;
	
	for(int i = 0; i < 26; i++){
		if(first[i] == -1){
			continue;
		}
		
		maxSoFar = Math.Max(maxSoFar, last[i] - first[i] - 1);
	}
	
	return maxSoFar;
}
```
