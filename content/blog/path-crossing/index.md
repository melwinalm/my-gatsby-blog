---
title: Path Crossing
date: "2020-06-28"
type: problem-solving
description: Path Crossing
tags: csharp
---

Note: This problem was taken from LeetCode - [Path Crossing](https://leetcode.com/problems/path-crossing/)

### Using HashSet

```csharp
public bool IsPathCrossing(string path) {
	HashSet<string> set = new HashSet<string>();
	
	set.Add("0$0");
	
	int currX = 0;
	int currY = 0;
	
	foreach(char c in path){
		if(c == 'N'){
			currY++;
		}
		else if(c == 'S'){
			currY--;
		}
		else if(c == 'E'){
			currX++;
		}
		else{
			currX--;
		}
		
		string newLoc = currX + "$" + currY;
		
		if(set.Contains(newLoc)){
			return true;
		}
		
		set.Add(newLoc);
	}
	
	return false;
}
```
