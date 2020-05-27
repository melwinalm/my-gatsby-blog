---
title: Contiguous Array
date: "2020-05-27"
type: problem-solving
description: Contiguous Array
tags: csharp
---

Note: This problem was taken from LeetCode - [Contiguous Array](https://leetcode.com/problems/contiguous-array/)

### Using Dictionary

```csharp
public int FindMaxLength(int[] nums) {
	Dictionary<int,int> map = new Dictionary<int,int>();
	
	map[0] = -1;
	
	int maxLength = 0;
	int count = 0;
	
	for(int i = 0; i < nums.Length; i++){
		if(nums[i] == 0){
			count++;
		}
		else{
			count--;
		}
		
		if(map.ContainsKey(count)){
			maxLength = Math.Max(maxLength, i - map[count]);
		}
		else{
			map[count] = i;
		}
	}
	
	return maxLength;
}
```
