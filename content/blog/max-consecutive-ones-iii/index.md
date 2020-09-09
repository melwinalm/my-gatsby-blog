---
title: Max Consecutive Ones III
date: "2020-09-07"
type: problem-solving
description: Max Consecutive Ones III
tags: csharp
---

Note: This problem was taken from LeetCode - [Max Consecutive Ones III](https://leetcode.com/problems/max-consecutive-ones-iii/)

### Using Two Pointer or Sliding Window Approach

```csharp
public int LongestOnes(int[] A, int K) {
	int n = A.Length;
	int sIndex = 0;
	int lIndex = 0;
	
	int usedK = 0;
	int maxSoFar = 0; 
	
	while(lIndex < n && sIndex < n){
		if(A[lIndex] == 0){
			if(usedK < K){
				maxSoFar = Math.Max(maxSoFar, lIndex - sIndex + 1);
				usedK++;
				lIndex++;
			}
			else{
				if(A[sIndex] == 0){
					usedK--;
				}
				sIndex++;
			}
		}
		else{
			maxSoFar = Math.Max(maxSoFar, lIndex - sIndex + 1);
			lIndex++;
		}
	}
	
	return maxSoFar;
}
```
