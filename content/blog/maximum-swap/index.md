---
title: Maximum Swap
date: "2020-09-09"
type: problem-solving
description: Maximum Swap
tags: csharp
---

Note: This problem was taken from LeetCode - [Maximum Swap](https://leetcode.com/problems/maximum-swap/)

### Using Greedy Approach

```csharp
public int MaximumSwap(int num) {
	int[] lastOne = new int[10];
	
	Array.Fill(lastOne, -1);
	
	List<int> nums = this.ConvertToArray(num);
	
	for(int i = 0; i < nums.Count; i++){
		lastOne[nums[i]] = i;
	}
	
	for(int i = 0; i < nums.Count; i++){
		for(int j = 9; j >= 1; j--){
			if(lastOne[j] != -1 && j > nums[i] && i < lastOne[j]){
				nums[lastOne[j]] = nums[i];
				nums[i] = j;
				
				return this.ConvertToNum(nums);
			}
		}
	}
	
	return this.ConvertToNum(nums);
}

public List<int> ConvertToArray(int num){
	List<int> output = new List<int>();
	
	while(num > 0){
		output.Add(num%10);
		num /= 10;
	}
	
	output.Reverse();
	
	return output;
}

public int ConvertToNum(List<int> nums){
	string num = "";
	
	for(int i = 0; i < nums.Count; i++){
		num += nums[i];
	}
	
	return Convert.ToInt32(num);
}
```
