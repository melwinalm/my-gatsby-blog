---
title: Sum of All Odd Length Subarrays
date: "2020-09-20"
type: problem-solving
description: Sum of All Odd Length Subarrays
tags: csharp
---

Note: This problem was taken from LeetCode - [Sum of All Odd Length Subarrays](https://leetcode.com/problems/sum-of-all-odd-length-subarrays/)

### Using Prefix Sum

```csharp
public int SumOddLengthSubarrays(int[] arr) {
	int N = arr.Length;
	
	int[] prefixSum = new int[N+1];
	
	for(int i = 1; i <= N; i++){
		prefixSum[i] = prefixSum[i-1] + arr[i-1];
	}
	
	int result = 0;
	
	for(int i = 0; i < N; i++){
		for(int j = i+1; j <= N; j+=2){
			result += prefixSum[j] - prefixSum[i];
		}
	}
	
	return result;
}
```
