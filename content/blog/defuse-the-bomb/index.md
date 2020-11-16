---
title: Defuse the Bomb
date: "2020-11-16"
type: problem-solving
description: Defuse the Bomb
tags: csharp
---

Note: This problem was taken from LeetCode - [Defuse the Bomb](https://leetcode.com/problems/defuse-the-bomb/)

### Straight Forward Solution

```csharp
public int[] Decrypt(int[] code, int k) {
	
	int N = code.Length;
	
	int[] output = new int[N];
	
	if(k == 0){
		return output;
	}
	else if(k < 0){
		for(int i = 0; i < N; i++){
			int count = 0;
			while(count < Math.Abs(k)){
				output[i] += code[(i - count - 1 + N)%N];
				count++;
			}
		}
	}
	else{
		for(int i = 0; i < N; i++){
			int count = 0;
			while(count < k){
				output[i] += code[(i + count + 1)%N];
				count++;
			}
		}
	}
	
	return output;
}
```
