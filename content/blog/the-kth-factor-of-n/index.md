---
title: The kth Factor of n
date: "2020-06-27"
type: problem-solving
description: The kth Factor of n
tags: csharp
---

Note: This problem was taken from LeetCode - [The kth Factor of n](https://leetcode.com/problems/the-kth-factor-of-n/)

### Using Math

Check all the factors of n starting from 1. Whenever a factor is found decrment k. Repeat this until k is 0 to get the required result.

```csharp
public int KthFactor(int n, int k) {
	int i = 1;
	
	while(k != 0 & i <= n){
		if(n % i == 0){
			k--;
		}
		i++;
	}
	
	return k == 0 ? i-1 : -1;
}
```
