---
title: Partition Equal Subset Sum
date: "2020-05-06"
type: problem-solving
description: Partition Equal Subset Sum
tags: csharp
---

Note: This problem was taken from LeetCode - [Partition Equal Subset Sum](https://leetcode.com/problems/partition-equal-subset-sum/)

### Using Top-Down Approach (Time limit exceeded)

First, find the sum of the given array. If the sum is odd then the array cannot be partitioned. If the sum is even, recursively check if you can get the half of the sum using 0/1 knapsack technique.

```csharp
public bool CanPartition(int[] nums) {
	int sum = 0;
	
	for(int i = 0; i < nums.Length; i++){
		sum += nums[i];
	}
	
	if(sum % 2 != 0){
		return false;
	}
	
	return this.CanPartition(nums, sum/2, 0);
}

public bool CanPartition(int[] nums, int remainingW, int currIndex){
	if(remainingW == 0 && currIndex == nums.Length){
		return true;
	}
	
	if (currIndex >= nums.Length){
		return false;
	}

	return this.CanPartition(nums, remainingW, currIndex + 1) || this.CanPartition(nums, remainingW - nums[currIndex], currIndex + 1);
}
```

### Using Memoization

Making a few changes to the above code using memoization will significantly improve the speed of the above code.

### Using Bottom-Up Approach

```csharp
public bool CanPartition(int[] nums) {
	int sum = 0;

	for(int i = 0; i < nums.Length; i++){
		sum += nums[i];
	}

	if(sum % 2 != 0){
		return false;
	}
	
	int reqSum = sum / 2;
	
	int n = nums.Length;
	
	bool[,] memo = new bool[n + 1,reqSum + 1];
	
	for(int i = 0; i < n+1; i++){
		memo[i,0] = true;
	}
	
	for(int w = 1; w < reqSum + 1; w++){
		memo[0,w] = false;
	}
	
	for(int i = 1; i < n+1; i++){
		for(int w = 1; w < reqSum + 1; w++){
			if (nums[i-1] > w){
				memo[i,w] = memo[i-1,w];
			}
			else{
				memo[i,w] = memo[i-1,w] || memo[i-1,w-nums[i-1]];
			}
		}
	}
	
	return memo[n, reqSum];
}
```

### Using Bottom Up (Space Optimized)

```csharp
public bool CanPartition(int[] nums) {
	int sum = 0;

	for(int i = 0; i < nums.Length; i++){
		sum += nums[i];
	}

	if(sum % 2 != 0){
		return false;
	}
	
	int reqSum = sum / 2;
	
	int n = nums.Length;
	
	bool[] memo = new bool[reqSum + 1];
	
	memo[0] = true;
	
	for(int i = 0; i < n; i++){
		for(int w = reqSum; w > 0; w--){
			if(w >= nums[i]){
				memo[w] = memo[w] || memo[w - nums[i]];
			}
		}
	}
	
	return memo[reqSum];
}
```
