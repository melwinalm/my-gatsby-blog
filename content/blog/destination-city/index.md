---
title: Destination City
date: "2020-05-03"
type: problem-solving
description: Destination City
tags: csharp
---

Note: This problem was taken from LeetCode - [Destination City](https://leetcode.com/problems/destination-city/)

### Dictionary Approach

Push all the from and to of a city path to a dictionary. Then iterate through the dictionary items and check if the value of a key is also a key in the dictionary. The value which isn't a key in the dictionary is the solution to this problem.

```csharp
public string DestCity(IList<IList<string>> paths) {
	Dictionary<string,string> map = new Dictionary<string, string>();
	
	for(int i = 0; i < paths.Count; i++){
		map[paths[i][0]] = paths[i][1];
	}
	
	foreach(var item in map){
		string Key = item.Key;
		
		while(true){
			if(map.ContainsKey(Key)){
				Key = map[Key];
			}
			else{
				return Key;
			}
		}
	}
		
	return "";
}
```
