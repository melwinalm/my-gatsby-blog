---
title: Ransom Note
date: "2020-05-03"
type: problem-solving
description: Ransom Note
tags: csharp
---

Note: This problem was taken from LeetCode - [Ransom Note](https://leetcode.com/problems/ransom-note/)

### Dictionary Approach

```csharp
public bool CanConstruct(string ransomNote, string magazine) {
	Dictionary<char, int> map = new Dictionary<char, int>();
	
	for(int i = 0; i < magazine.Length; i++){
		if(map.ContainsKey(magazine[i])){
			map[magazine[i]] += 1;
		}
		else{
			map[magazine[i]] = 1;
		}
	}
	
	for(int i = 0; i < ransomNote.Length; i++){
		if(map.ContainsKey(ransomNote[i]) && map[ransomNote[i]] > 0){
			map[ransomNote[i]] -= 1;
		}
		else{
			return false;
		}
	}
	
	return true;
}
```
