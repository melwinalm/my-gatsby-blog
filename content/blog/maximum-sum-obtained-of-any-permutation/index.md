---
title: Maximum Sum Obtained of Any Permutation
date: "2020-09-20"
type: problem-solving
description: Maximum Sum Obtained of Any Permutation
tags: csharp
---

Note: This problem was taken from LeetCode - [Maximum Sum Obtained of Any Permutation](https://leetcode.com/problems/maximum-sum-obtained-of-any-permutation/)

### Using Frequency Count and Sorting (Time Limit Exceeded)

This method uses nested loops to find the frequency count of ranges.

```csharp
public int MaxSumRangeQuery(int[] nums, int[][] requests) {
	int N = nums.Length;
	
	int[] freq = new int[N];
	
	int M = 1000000007;
	
	foreach(int[] request in requests){
		for(int i = request[0]; i <= request[1]; i++){
			freq[i]++;
		}
	}
	
	Array.Sort(nums);
	Array.Sort(freq);
	
	long result = 0;
	
	for(int i = 0; i < N; i++){
		result = result + (nums[i] * freq[i]);
	}
	
	return (int)(result % M);        
}
```

### Using Frequency Count and Sorting (Improved)

This method uses prefix sum approach to find the frequency count of the ranges.

```csharp
public int MaxSumRangeQuery(int[] nums, int[][] requests) {
	int N = nums.Length;
	
	int[] freq = new int[N];
	
	int M = 1000000007;
	
	for(int i = 0; i < requests.Length; i++){
		int start = requests[i][0];
		int end = requests[i][1];
		
		freq[start]++;
		
		if(end+1 < N){
			freq[end+1]--;
		}
	}
	
	int[] prefixSum = new int[N];
	int tempSum = 0;
	
	for(int i = 0; i < N; i++){
		tempSum += freq[i];
		prefixSum[i] = tempSum;
	}
	
	Array.Sort(nums);
	Array.Sort(prefixSum);
	
	long result = 0;
	
	for(int i = 0; i < N; i++){
		result = result + (nums[i] * prefixSum[i]);
	}
	
	return (int)(result % M);        
}
```
