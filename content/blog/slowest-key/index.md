---
title: Slowest Key
date: "2020-10-25"
type: problem-solving
description: Slowest Key
tags: csharp
---

Note: This problem was taken from LeetCode - [Slowest Key](https://leetcode.com/problems/slowest-key/)

### Naive Approach

```csharp
public char SlowestKey(int[] releaseTimes, string keysPressed) {
	int prev = releaseTimes[0];
	char output = keysPressed[0];
	int maxDist = releaseTimes[0];
	
	for(int i = 1; i < releaseTimes.Length; i++){
		int diff = releaseTimes[i] - prev;
		
		if(diff > maxDist || (diff == maxDist && keysPressed[i] > output)){
			maxDist = diff;
			output = keysPressed[i];
		}
		
		prev = releaseTimes[i];
	}
	
	return output;
}
```
