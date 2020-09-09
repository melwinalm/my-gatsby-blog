---
title: Compare Version Numbers
date: "2020-09-09"
type: problem-solving
description: Compare Version Numbers
tags: csharp
---

Note: This problem was taken from LeetCode - [Compare Version Numbers](https://leetcode.com/problems/compare-version-numbers/)

### Naive Approach

```csharp
public int CompareVersion(string version1, string version2) {
	List<int> ver1 = this.ConvertVersion(version1);
	List<int> ver2 = this.ConvertVersion(version2);
	
	if(ver1.Count > ver2.Count){
		int diff = ver1.Count - ver2.Count;
		for(int i = 0; i < diff; i++){
			ver2.Add(0);
		}
	}
	else if(ver2.Count > ver1.Count){
		int diff = ver2.Count - ver1.Count;
		for(int i = 0; i < diff; i++){
			ver1.Add(0);
		}
	}
	
	for(int i = 0; i < ver1.Count; i++){
		if(ver1[i] == ver2[i]){
			continue;
		}
		else if(ver1[i] > ver2[i]){
			return 1;
		}
		else{
			return -1;
		}
	}
	
	return 0;
}

public List<int> ConvertVersion(string version){
	string[] splits = version.Split(".");
	List<int> output = new List<int>();

	for(int i = 0; i < splits.Length; i++){
		output.Add(Convert.ToInt32(splits[i]));
	}
	
	return output;
}
```
