---
title: Find All Anagrams in a String
date: "2020-05-18"
type: problem-solving
description: People Find All Anagrams in a String
tags: csharp
---

Note: This problem was taken from LeetCode - [Find All Anagrams in a String](https://leetcode.com/problems/find-all-anagrams-in-a-string/)

### Using Sliding Window Technique

```csharp
public IList<int> FindAnagrams(string s, string p) {
	List<int> output = new List<int>();
	
	if(s.Length == 0 || p.Length == 0){
		return output;
	}
	
	Dictionary<char, int> map = new Dictionary<char, int>();
	
	foreach(char c in p){
		if(map.ContainsKey(c)){
			map[c] += 1;
		}
		else{
			map[c] = 1;
		}
	}
	
	int start = 0;
	int end = 0;
	int count = map.Count;
	
	while(end < s.Length){
		char c = s[end];
		if(map.ContainsKey(c)){
			map[c] = map[c] - 1;
			if(map[c] == 0){
				count--;
			}
		}
		end++;
		
		while(count == 0){
			char c2 = s[start];
			if(map.ContainsKey(c2)){
				map[c2] = map[c2] + 1;
				if(map[c2] > 0){
					count++;
				}    
			}
				
			if(end - start == p.Length){
				output.Add(start);
			}   
			start++;
		}
	}
	
	return output;        
}  
```
