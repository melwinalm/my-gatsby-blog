---
title: Minimum Deletions to Make String Balanced
date: "2020-11-16"
type: problem-solving
description: Minimum Deletions to Make String Balanced
tags: csharp
---

Note: This problem was taken from LeetCode - [Minimum Deletions to Make String Balanced](https://leetcode.com/problems/minimum-deletions-to-make-string-balanced/)

### Greedy Approach

```csharp
public int MinimumDeletions(string s) {
	int aCount = 0;
	int bCount = 0;
	
	foreach(char c in s){
		if(c == 'a'){
			aCount++;
		}
	}
	
	int minSoFar = aCount;

	foreach(char c in s){
		if(c == 'a'){
			aCount--;
		}
		else{
			bCount++;
		}
		
		minSoFar = Math.Min(minSoFar, aCount + bCount);
	}
	
	return minSoFar;
}
```
