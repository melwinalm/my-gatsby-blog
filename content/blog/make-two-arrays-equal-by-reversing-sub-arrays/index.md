---
title: Make Two Arrays Equal by Reversing Sub-arrays
date: "2020-05-30"
type: problem-solving
description: Make Two Arrays Equal by Reversing Sub-arrays
tags: csharp
---

Note: This problem was taken from LeetCode - [Make Two Arrays Equal by Reversing Sub-arrays](https://leetcode.com/problems/make-two-arrays-equal-by-reversing-sub-arrays/)

### Using Dictionary

```csharp
public bool CanBeEqual(int[] target, int[] arr) {
	Dictionary<int, int> map = new Dictionary<int, int>();
	
	foreach(int item in arr){
		if(!map.ContainsKey(item)){
			map[item] = 0;
		}
		
		map[item] += 1;
	}
	
	foreach(int item in target){
		if(!map.ContainsKey(item)){
			return false;
		}
		else{
			if(map[item] > 0){
				map[item] -= 1;
			}
			else{
				return false;
			}
		}
	}
	
	return true;
}
```
