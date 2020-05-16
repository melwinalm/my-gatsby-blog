---
title: Maximum Sum Circular Subarray
date: "2020-05-16"
type: problem-solving
description: Maximum Sum Circular Subarray
tags: csharp
---

Note: This problem was taken from LeetCode - [Maximum Sum Circular Subarray](https://leetcode.com/problems/maximum-sum-circular-subarray/)

### Using Kadane's Algorithm

```csharp
public int MaxSubarraySumCircular(int[] A) {
	// Edge case when array length is 1
	if(A.Length == 1){
		return A[0];
	}
	
	int totalSum = A[0];
	int currMaxSum = A[0];
	int currMinSum = A[0];
	int maxSum = A[0];
	int minSum = A[1];
	
	for(int i = 1; i < A.Length; i++){
		totalSum += A[i];
		currMaxSum = Math.Max(currMaxSum + A[i], A[i]);
		currMinSum = Math.Min(currMinSum + A[i], A[i]);
		
		maxSum = Math.Max(maxSum, currMaxSum);
		minSum = Math.Min(minSum, currMinSum);
	}
	
	int output = Math.Max(maxSum, totalSum - minSum);
	
	// Case when all the elements of the array are negative, the output will be zero. 
	if(output == 0){
		return maxSum;
	}
	
	return output;
}
```
