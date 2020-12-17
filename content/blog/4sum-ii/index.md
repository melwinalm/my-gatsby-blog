---
title: 4Sum II
date: "2020-12-17"
type: problem-solving
description: 4Sum II
---

Note: This problem was taken from LeetCode - [4Sum II](https://leetcode.com/problems/4sum-ii/)

### Quadratic Time and Space Complexity

```csharp
public int FourSumCount(int[] A, int[] B, int[] C, int[] D) {
	Dictionary<int,int> map = new Dictionary<int,int>();
	
	for(int i = 0; i < A.Length; i++){
		for(int j = 0; j < B.Length; j++){
			int sum = A[i] + B[j];
			
			if(!map.ContainsKey(sum)){
				map[sum] = 0;
			}
			map[sum]++;
		}
	}
	
	int output = 0;
	
	for(int i = 0; i < C.Length; i++){
		for(int j = 0; j < D.Length; j++){
			int sum = -1 * (C[i] + D[j]);
			
			if(map.ContainsKey(sum)){
				output += map[sum];
			}
		}
	}
	
	return output;
}
```
