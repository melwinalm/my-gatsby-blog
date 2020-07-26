---
title: Bulb Switcher IV
date: "2020-07-26"
type: problem-solving
description: Bulb Switcher IV
tags: csharp
---

Note: This problem was taken from LeetCode - [Bulb Switcher IV](https://leetcode.com/problems/bulb-switcher-iv/)

### Using greedy Approach

```csharp
public int MinFlips(string target) {
	int flips = 0;
	
	char curr = '0';
	
	foreach(char c in target){
		if(curr != c){
			flips++;
			curr = c;
		}
	}
	
	return flips;
}
```
