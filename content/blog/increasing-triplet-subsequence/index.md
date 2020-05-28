---
title: Increasing Triplet Subsequence
date: "2020-05-28"
type: problem-solving
description: Increasing Triplet Subsequence
tags: csharp
---

Note: This problem was taken from LeetCode - [Increasing Triplet Subsequence](https://leetcode.com/problems/increasing-triplet-subsequence/)

### Naive Solution

```csharp
public bool IncreasingTriplet(int[] nums)
{
	int min = Int32.MaxValue;
	int max = Int32.MaxValue;
	
	foreach(int n in nums){
		if(n <= min){
			min = n;
		}
		else if (n <= max){
			max = n;
		}
		else{
			return true;
		}
	}
	
	return false;
}
```

### Bottom Up Approach (Generic Solution - holds good for any number of increasing subsequence)

```csharp
public bool IncreasingTriplet(int[] nums)
{
	int n = nums.Length;

	if (n <= 2)
	{
		return false;
	}

	int[] dp = new int[n+1];

	for (int i = 1; i <= n; i++)
	{
		for (int j = 1; j < i; j++)
		{
			if (nums[i-1] > nums[j-1])
			{
				dp[i] = Math.Max(dp[i], 1 + dp[j]);

				if (dp[i] >= 2)
				{
					return true;
				}
			}
		}
	}

	return false;
}
```
