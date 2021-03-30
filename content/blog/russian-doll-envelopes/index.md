---
title: Russian Doll Envelopes
date: "2021-03-30"
type: problem-solving
description: Russian Doll Envelopes
tags: csharp
---

Note: This problem was taken from LeetCode - [Russian Doll Envelopes](https://leetcode.com/problems/russian-doll-envelopes/)

### Using Dynamic Programming

```csharp
public int MaxEnvelopes(int[][] envelopes) {
	Array.Sort(envelopes, (a,b) => a[0] == b[0] ? a[1] - b[1] : a[0] - b[0]);
	
	int N = envelopes.Length;
	
	int[] memo = new int[N];
	
	memo[0] = 1;
	
	for(int i = 1; i < N; i++){
		memo[i] = 1;
		
		int[] curr = envelopes[i];
		
		for(int j = 0; j < i; j++){
			int[] prev = envelopes[j];
			int prevMemo = memo[j];
			
			if(prev[0] < curr[0] && prev[1] < curr[1]){
				if(prevMemo + 1 > memo[i]){
					memo[i] = 1 + prevMemo;
				}
			}
			
		}
	}
	
	return memo.Max();
}
```
