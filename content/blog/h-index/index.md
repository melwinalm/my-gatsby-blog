---
title: H-Index
date: "2020-08-11"
type: problem-solving
description: H-Index
tags: csharp
---

Note: This problem was taken from LeetCode - [H-Index](https://leetcode.com/problems/h-index/)

```csharp
public int HIndex(int[] citations) {
	int N = citations.Length;
	Array.Sort(citations);
	
	for(int i = 0; i < N; i++){
		if(citations[i] >= N-i){
			return N-i;
		}
	}
	
	return 0;
}
```
