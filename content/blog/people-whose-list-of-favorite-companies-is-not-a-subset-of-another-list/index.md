---
title: People Whose List of Favorite Companies Is Not a Subset of Another List
date: "2020-05-17"
type: problem-solving
description: People Whose List of Favorite Companies Is Not a Subset of Another List
tags: csharp
---

Note: This problem was taken from LeetCode - [People Whose List of Favorite Companies Is Not a Subset of Another List](https://leetcode.com/problems/people-whose-list-of-favorite-companies-is-not-a-subset-of-another-list/)

### Brute Force Method

```csharp
public IList<int> PeopleIndexes(IList<IList<string>> favoriteCompanies) {
	List<int> output = new List<int>();
	
	bool[] boolArray = new bool[favoriteCompanies.Count];

	for(int i = 0; i < favoriteCompanies.Count; i++){
		HashSet<string> map = new HashSet<string>();
		foreach(string word in favoriteCompanies[i]){
			map.Add(word);
		}
		for(int j = 0; j < favoriteCompanies.Count; j++){
			if(i != j ){
				if(boolArray[j] == true){
					continue;
				}
				boolArray[j] = boolArray[j] || this.IsSubset(favoriteCompanies, j, map);
			}
		}
	}
	
	for(int i = 0; i < boolArray.Length; i++){
		if(boolArray[i] == false){
			output.Add(i);
		}
	}
	
	return output;
}

public bool IsSubset(IList<IList<string>> fc, int child, HashSet<string> map){
	if(fc[child].Count > map.Count){
		return false;
	}
	
	foreach(string item in fc[child]){
		if(!map.Contains(item)){
			return false;
		}
	}
	
	return true;
}  
```
