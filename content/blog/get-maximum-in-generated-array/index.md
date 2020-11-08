---
title: Get Maximum in Generated Array
date: "2020-11-08"
type: problem-solving
description: Get Maximum in Generated Array
tags: csharp
---

Note: This problem was taken from LeetCode - [Get Maximum in Generated Array](https://leetcode.com/problems/get-maximum-in-generated-array/)

### Linear Space Solution

```csharp
public int GetMaximumGenerated(int n) {
	if(n == 0){
		return 0;
	}
	
	int[] arr = new int[n+1];
	
	int max = 1;
	
	arr[0] = 0;
	arr[1] = 1;
	
	for(int i = 2; i <= n; i++){
		if(i % 2 == 0){
			arr[i] = arr[i/2];
		}
		else{
			arr[i] = arr[i/2] + arr[(i/2)+1];
		}
		
		max = Math.Max(arr[i], max);
	}
	
	return max;
}
```
