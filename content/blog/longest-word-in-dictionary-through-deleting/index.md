---
title: Longest Word in Dictionary through Deleting
date: "2021-02-23"
type: problem-solving
description: Longest Word in Dictionary through Deleting
tags: csharp
---

Note: This problem was taken from LeetCode - [Longest Word in Dictionary through Deleting](https://leetcode.com/problems/longest-word-in-dictionary-through-deleting/)

### Using Sorting

```csharp
public string FindLongestWord(string s, IList<string> d) {
	string output = "";
	
	List<string> dCopy = new List<string>(d);
	// Sorting the list in the descending and lexicographical order
	dCopy.Sort((a,b) => a.Length == b.Length ? a.CompareTo(b) : b.Length - a.Length);
	
	foreach(string item in dCopy){
		if(IsSubsequence(s, item)){
			return item;
		}    
	}
	
	return output;        
}

public bool IsSubsequence(string s, string d){
	if(d.Length > s.Length){
		return false;
	}
	
	int i = 0;
	int j = 0;
	
	while(i < s.Length && j < d.Length){
		if(s[i] == d[j]){
			j++;
		}
		i++;
	}
	
	return j == d.Length;        
}
```

### Without Sorting

```csharp
public string FindLongestWord(string s, IList<string> d) {
	string output = "";
	
	foreach(string item in d){
		if(IsSubsequence(s, item)){
			if(item.Length > output.Length || (item.Length == output.Length && item.CompareTo(output) < 1)){
				output = item;                    
			}                
		}    
	}
	
	return output;        
}

public bool IsSubsequence(string s, string d){
	if(d.Length > s.Length){
		return false;
	}
	
	int i = 0;
	int j = 0;
	
	while(i < s.Length && j < d.Length){
		if(s[i] == d[j]){
			j++;
		}
		i++;
	}
	
	return j == d.Length;        
}  
```
