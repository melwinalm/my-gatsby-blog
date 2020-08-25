---
title: Maximize Sum Of Array After K Negations
date: "2020-08-25"
type: problem-solving
description: Maximize Sum Of Array After K Negations
tags: csharp
---

Note: This problem was taken from LeetCode - [Maximize Sum Of Array After K Negations](https://leetcode.com/problems/maximize-sum-of-array-after-k-negations/)

### Greedy Approach

```csharp
public int LargestSumAfterKNegations(int[] A, int K) {
	Array.Sort(A);
	
	for(int i = 0; i < A.Length && K > 0; i++){
		if(A[i] < 0){
			A[i] = -A[i];
			K--;
		}
	}
	
	if(K % 2 == 1){
		return this.ArraySum(A) - (2 * this.MinElement(A));
	}
	else{
		return this.ArraySum(A);
	}
}

public int ArraySum(int[] A){
	int sum = 0;
	
	foreach(int item in A){
		sum += item;
	}
	
	return sum;
}

public int MinElement(int[] A){
	int min = Int32.MaxValue;
	
	foreach(var item in A){
		min = Math.Min(min, item);
	}
	
	return min;
}
```
