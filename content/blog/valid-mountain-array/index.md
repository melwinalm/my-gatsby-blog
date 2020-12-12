---
title: Valid Mountain Array
date: "2020-12-12"
type: problem-solving
description: Valid Mountain Array
---

Note: This problem was taken from LeetCode - [Valid Mountain Array](https://leetcode.com/problems/valid-mountain-array/)

### Naive Approach

```csharp
public bool ValidMountainArray(int[] arr) {
	if(arr.Length < 3){
		return false;
	}
	
	int i = 1;
	
	while(i < arr.Length){
		if(arr[i-1] < arr[i]){
			i++;
			continue;
		}
		else if(arr[i-1] == arr[i]){
			return false;
		}
		else{
			break;
		}
		
	}
	
	if(i == arr.Length || i == 1){
		return false;
	}
	
	while(i < arr.Length){
		if(arr[i-1] > arr[i]){
			i++;
			continue;
		}
		else{
			return false;
		}
	}
	
	return true;
}
```
