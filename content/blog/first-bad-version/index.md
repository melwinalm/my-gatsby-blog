---
title: First Bad Version
date: "2020-05-21"
type: problem-solving
description: First Bad Version
tags: csharp
---

Note: This problem was taken from LeetCode - [First Bad Version](https://leetcode.com/problems/first-bad-version/)

### Using Binary Search

```csharp
public int FirstBadVersion(int n) {
	int low = 1;
	int high = n;
	
	while(low < high){
		int mid = low + ((high - low)/2);
				
		bool isBad = this.IsBadVersion(mid);
		
		if(isBad){
			high = mid;
		}
		else{
			low = mid + 1;
		}
	}
	
	return low;
}
```
