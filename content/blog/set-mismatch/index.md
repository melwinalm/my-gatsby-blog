---
title: Set Mismatch
date: "2021-03-02"
type: problem-solving
description: Set Mismatch
tags: csharp
---

Note: This problem was taken from LeetCode - [Set Mismatch](https://leetcode.com/problems/set-mismatch/)

### Using Frequency Count

```csharp
public int[] FindErrorNums(int[] nums) {
	int N = nums.Length;
	
	int[] freq = new int[N+1];
	
	// Finding the frequency of all numbers in the array
	for(int i = 0; i < N; i++){
		freq[nums[i]]++;
	}
	
	int missing = 0;
	int repeat = 0;
	
	
	for(int i = 1; i < freq.Length; i++){
		if(freq[i] > 1){
			repeat = i;
		}
		else if(freq[i] == 0){
			missing = i;
		}
	}
	
	return new int[] {repeat, missing};
}
```
