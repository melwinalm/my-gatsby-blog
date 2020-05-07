---
title: Verifying an Alien Dictionary
date: "2020-05-07"
type: problem-solving
description: Verifying an Alien Dictionary
tags: csharp
---

Note: This problem was taken from LeetCode - [Verifying an Alien Dictionary](https://leetcode.com/problems/verifying-an-alien-dictionary/)

### Using Dictionary
```csharp
public bool IsAlienSorted(string[] words, string order) {
	if(words.Length <= 1){
		return true;
	}
	
	Dictionary<char, int> map = new Dictionary<char, int>();
	
	for(int i = 0; i < order.Length; i++){
		map[order[i]] = i;
	}
	
	for(int i = 1; i < words.Length; i++){
		int index = Math.Min(words[i-1].Length, words[i].Length);
		
		int flag = 0;
		for(int j = 0; j < index; j++){
			if(map[words[i-1][j]] > map[words[i][j]]){
				return false;
			}
			else if(map[words[i-1][j]] < map[words[i][j]]){
				break;
			}
			
			if(words[i-1][j] == words[i][j]){
				flag++;
			}
		}
		
		if(flag == index && words[i-1].Length > words[i].Length){
			return false;
		}
	}
	
	return true;
}
```
