---
title: Permutation in String
date: "2020-05-18"
type: problem-solving
description: Permutation in String
tags: csharp
---

Note: This problem was taken from LeetCode - [Permutation in String](https://leetcode.com/problems/permutation-in-string/)

### Using Sliding Window Technique

```csharp
public bool CheckInclusion(string s1, string s2) {
	Dictionary<char, int> freqs = new Dictionary<char, int>();
	
	foreach(char c in s1){
		if(freqs.ContainsKey(c)){
			freqs[c] += 1;
		}
		else{
			freqs[c] = 1;
		}
	}
	
	int start = 0;
	int end = 0;
	int size = freqs.Count;
	
	while(end < s2.Length){
		char c = s2[end];
		
		if(freqs.ContainsKey(c)){
			freqs[c] = freqs[c] - 1;
			if(freqs[c] == 0){
				size--;
			}
		}
		end++;
		
		while(size == 0){
			char c2 = s2[start];
			
			if(freqs.ContainsKey(c2)){
				freqs[c2] = freqs[c2] + 1;
				if(freqs[c2] > 0){
					size++;
				}
			}
			
			if(end - start == s1.Length){
				return true;
			}
			start++;
		}
	}
	
	return false;
}
```
