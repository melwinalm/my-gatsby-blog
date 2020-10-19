---
title: Repeated DNA Sequences
date: "2020-10-19"
type: problem-solving
description: Repeated DNA Sequences
tags: csharp
---

Note: This problem was taken from LeetCode - [Repeated DNA Sequences](https://leetcode.com/problems/repeated-dna-sequences/)

### Using HashSet

```csharp
public IList<string> FindRepeatedDnaSequences(string s) {
	HashSet<string> result = new HashSet<string>();
	HashSet<string> set = new HashSet<string>();
	
	if(s.Length <= 10){
		return result.ToList();
	}
	
	for(int i = 0; i < s.Length - 9; i++){
		string curr = s.Substring(i, 10);
		
		if(!set.Contains(curr)){
			set.Add(curr);
			continue;
		}
		
		if(!result.Contains(curr)){
			result.Add(curr);
		}
		
	}
	
	return result.ToList();
}
```
