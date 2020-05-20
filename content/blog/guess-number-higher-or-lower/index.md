---
title: Guess Number Higher or Lower
date: "2020-05-20"
type: problem-solving
description: Guess Number Higher or Lower
tags: csharp
---

Note: This problem was taken from LeetCode - [Guess Number Higher or Lower](https://leetcode.com/problems/guess-number-higher-or-lower/)

### Using Binary Search

```csharp
public int GuessNumber(int n) {
	int low = 1;
	int high = n;
	
	while(low <= high){
		int mid = low + ((high - low)/2);
		
		int apiResponse = this.guess(mid);
		
		if(apiResponse == 0){
			return mid;
		}
		else if(apiResponse == -1){
			high = mid - 1;
		}
		else if(apiResponse == 1){
			low = mid + 1;
		}
	}
	
	return -1;
}
```
