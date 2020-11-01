---
title: Check Array Formation Through Concatenation
date: "2020-11-01"
type: problem-solving
description: Check Array Formation Through Concatenation
tags: csharp
---

Note: This problem was taken from LeetCode - [Check Array Formation Through Concatenation](https://leetcode.com/problems/check-array-formation-through-concatenation/)

### Using Dictionary

```csharp
public bool CanFormArray(int[] arr, int[][] pieces) {
	Dictionary<int,int> map = new Dictionary<int,int>();
	
	for(int k = 0; k < pieces.Length; k++){
		map[pieces[k][0]] = k;
	}
	
	int i = 0;
	while(i < arr.Length){
		if(!map.ContainsKey(arr[i])){
			return false;
		}
		
		int pieceIndex = map[arr[i]];
		int size = pieces[pieceIndex].Length;
		
		int a = 0;
		
		while(a < size){
			if(arr[i] != pieces[pieceIndex][a]){
				return false;
			}
			a++;
			i++;
		}
		
	}
	
	return true;
}
```
