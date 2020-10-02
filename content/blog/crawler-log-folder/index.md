---
title: Crawler Log Folder
date: "2020-10-27"
type: problem-solving
description: Crawler Log Folder
tags: csharp
---

Note: This problem was taken from LeetCode - [Crawler Log Folder](https://leetcode.com/problems/crawler-log-folder/)

### Using One Pass

```csharp
public int MinOperations(string[] logs) {
	int count = 0;
	
	foreach(string log in logs){
		if(log == "../"){
			if(count != 0){
				count--;
			}
		}
		else if(log != "./"){
			count++;
		}
	}
	
	return count;
}
```
