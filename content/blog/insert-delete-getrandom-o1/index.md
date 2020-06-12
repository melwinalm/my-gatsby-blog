---
title: Insert Delete GetRandom O(1)
date: "2020-06-12"
type: problem-solving
description: Insert Delete GetRandom O(1)
tags: csharp
---

Note: This problem was taken from LeetCode - [Insert Delete GetRandom O(1)](https://leetcode.com/problems/insert-delete-getrandom-o1/)

### Using Recursive Approach

```csharp
Random rnd;
Dictionary<int, int> dict;
List<int> lst;

public RandomizedSet() {
	rnd = new Random();
	lst = new List<int>();
	dict = new Dictionary<int,int>();
}

public bool Insert(int val) {
	if(dict.ContainsKey(val)){
		return false;
	}
	
	lst.Add(val);
	int index = lst.Count - 1;
	
	dict[val] = index;
	
	return true;        
}

public bool Remove(int val) {
	if(!dict.ContainsKey(val)){
		return false;
	}

	// Swap the last item in the list with the given numbers' index value
	int index = dict[val];
	lst[index] = lst[lst.Count-1];
	dict[lst[index]] = index;
	
	// Remove the last item from thst list
	lst.RemoveAt(lst.Count - 1);
	dict.Remove(val);
	return true;
}

public int GetRandom() {
	int randomIndex = rnd.Next(0,lst.Count);
	return lst[randomIndex];
}
```
