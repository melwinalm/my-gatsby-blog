---
title: Minimum Deletions to Make Character Frequencies Unique
date: "2020-11-08"
type: problem-solving
description: Minimum Deletions to Make Character Frequencies Unique
tags: csharp
---

Note: This problem was taken from LeetCode - [Minimum Deletions to Make Character Frequencies Unique](https://leetcode.com/problems/minimum-deletions-to-make-character-frequencies-unique/)

### Greedy Solution

```csharp
public int MinDeletions(string s) {
	Dictionary<char,int> map = new Dictionary<char,int>();
	
	foreach(char c in s){
		if(!map.ContainsKey(c)){
			map[c] = 0;
		}
		
		map[c]++;
	}
	
	HashSet<int> set = new HashSet<int>();
	
	int result = 0;
	
	foreach(var item in map){
		int count = item.Value;
		
		while(set.Contains(count)){
			count--;
			result++;
		}
		
		if(count != 0){
			set.Add(count);
		}
	}

	return result;
}
```
