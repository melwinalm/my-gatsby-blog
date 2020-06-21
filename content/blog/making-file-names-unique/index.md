---
title: Making File Names Unique
date: "2020-06-21"
type: problem-solving
description: Making File Names Unique
tags: csharp
---

Note: This problem was taken from LeetCode - [Making File Names Unique](https://leetcode.com/problems/making-file-names-unique/)

### Using Dictionary

```csharp
public string[] GetFolderNames(string[] names) {
	int N = names.Length;
	
	string[] output = new string[N];
	
	Dictionary<string, int> map = new Dictionary<string,int>();
	
	for(int i = 0; i < N; i++){
		string currName = names[i];
		
		if(map.ContainsKey(names[i])){
			string tempName = currName + "(" + map[currName] + ")";
			
			while(map.ContainsKey(tempName)){
				map[currName]++;
				tempName = currName + "(" + map[currName] + ")";
			}
			
			output[i] = tempName;
		}
		else{
			output[i] = currName;
			map[currName] = 1;
		}
		
		map[output[i]] = 1;
	}
	
	return output;
}
```
