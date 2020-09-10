---
title: Find Common Characters
date: "2020-09-10"
type: problem-solving
description: Find Common Characters
tags: csharp
---

Note: This problem was taken from LeetCode - [Find Common Characters](https://leetcode.com/problems/find-common-characters/)

### Naive Approach

```csharp
public IList<string> CommonChars(string[] A) {
	List<string> output = new List<string>();
	
	int[] count = new int[26];
	
	Array.Fill(count, 200);
	
	foreach(string word in A){
		
		int[] tempCount = new int[26];
		
		foreach(char c in word){
			int val = c - 'a';
			tempCount[val] += 1;
		}
		
		for(int i = 0; i < 26; i++){
			count[i] = Math.Min(count[i], tempCount[i]);
		}
	}
	
	for(int i = 0; i < 26; i++){
		if(count[i] == 200 || count[i] == 0){
			continue;
		}
		
		char c = Convert.ToChar(97 + i);
		
		for(int j = 0; j < count[i]; j++){
			output.Add(c.ToString());
		}
	}
	
	
	return output;
}
```
