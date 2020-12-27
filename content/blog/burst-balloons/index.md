---
title: Burst Balloons
date: "2020-12-27"
type: problem-solving
description: Burst Balloons
---

Note: This problem was taken from LeetCode - [Burst Balloons](https://leetcode.com/problems/burst-balloons/)

### Dynamic Programming

```csharp
public int MaxCoins(int[] nums) {
	List<int> numList = new List<int>();
	numList.Add(1);
	numList.AddRange(nums.ToList());
	numList.Add(1);
	
	int N = numList.Count;
	
	int[,] dp = new int[N,N];
	
	for(int i = 1; i <= N-2; i++){
		for(int left = 1; left < N - i; left++){
			int right = left + i - 1;
			
			for(int j = left; j <= right; j++){
				int res = numList[left-1] * numList[j] * numList[right+1] + dp[left, j-1] + dp[j+1, right];
				dp[left, right] = Math.Max(dp[left, right], res);
			}
		}
	}
	
	return dp[1, N-2];
}
```
