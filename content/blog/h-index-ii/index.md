---
title: H-Index II
date: "2020-06-18"
type: problem-solving
description: H-Index II
tags: csharp
---

Note: This problem was taken from LeetCode - [H-Index II](https://leetcode.com/problems/h-index-ii/)

### Using Binary Search

```csharp
public int HIndex(int[] citations) {
	int N = citations.Length;
	int low = 0;
	int high = N - 1;
	int mid = 0;
	
	while(low <= high){
		mid = low + (high-low)/2;
		
		if(citations[mid] >= (N-mid)){
			high = mid - 1;
		}
		else{
			low = mid + 1;
		}
	}
	
	return N-low;
}
```
