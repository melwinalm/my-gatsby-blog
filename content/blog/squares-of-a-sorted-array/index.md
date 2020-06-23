---
title: Squares of a Sorted Array
date: "2020-06-22"
type: problem-solving
description: Squares of a Sorted Array
tags: csharp
---

Note: This problem was taken from LeetCode - [Squares of a Sorted Array](https://leetcode.com/problems/squares-of-a-sorted-array/)

### Using Two Pointer Approach

```csharp
public int[] SortedSquares(int[] A) {
	int N = A.Length;
	
	int[] output = new int[N];
	
	int sIndex = 0;
	int eIndex = N - 1;
	
	int outIndex = N-1;
	
	while(outIndex >= 0){
		int absS = Math.Abs(A[sIndex]);
		int absE = Math.Abs(A[eIndex]);
		
		int large;
		
		if(absS < absE){
			large = absE;
			eIndex--;
		}
		else{
			large = absS;
			sIndex++;
		}
		
		output[outIndex] = large * large;
		outIndex--;
	}
	
	return output;
}
```
