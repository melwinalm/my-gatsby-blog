---
title: Unique Morse Code Words
date: "2020-11-23"
type: problem-solving
description: Unique Morse Code Words
tags: csharp
---

Note: This problem was taken from LeetCode - [Unique Morse Code Words](https://leetcode.com/problems/unique-morse-code-words/)

### Using HashSet

```csharp
public int UniqueMorseRepresentations(string[] words) {
	string[] MorseCode = new string[] {".-","-...","-.-.","-..",".","..-.","--.","....","..",".---","-.-",".-..","--","-.","---",".--.","--.-",".-.","...","-","..-","...-",".--","-..-","-.--","--.."};
	
	HashSet<string> seen = new HashSet<string>();
	
	foreach(string word in words){
		StringBuilder code = new StringBuilder();
		
		foreach(char c in word){
			code.Append(MorseCode[c - 'a']);
		}
		seen.Add(code.ToString());
	}
	
	return seen.Count;
}
```
