---
title: Summary Ranges
date: "2020-10-28"
type: problem-solving
description: Summary Ranges
tags: csharp
---

Note: This problem was taken from LeetCode - [Summary Ranges](https://leetcode.com/problems/summary-ranges/)

### Naive Approach

```csharp
public IList<string> SummaryRanges(int[] nums) {
	List<string> output = new List<string>();
	
	if(nums.Length == 0){
		return output;
	}
	
	int start = nums[0];
	int prev = nums[0];
	int i = 0;
	
	while(i < nums.Length){
		if((long)nums[i] - (long)prev > 1){
			if(start == prev){
				output.Add(start.ToString());
			}
			else{
				output.Add(start.ToString() + "->" + prev.ToString());
			}
			
			start = nums[i];
			prev = nums[i];
		}
		else{
			prev = nums[i];
			i++;
		}
	}
	
	if(start == prev){
		output.Add(start.ToString());
	}
	else{
		output.Add(start.ToString() + "->" + prev.ToString());
	}
	
	return output;
}
```

### Naive Approach (Code Improved)

```csharp
public IList<string> SummaryRanges(int[] nums) {
	List<string> output = new List<string>();
	
	if(nums.Length == 0){
		return output;
	}
	
	int start = nums[0];
	int prev = nums[0];
	int i = 0;
	
	while(i <= nums.Length){
		if(i == nums.Length || (long)nums[i] - (long)prev > 1){
			if(start == prev){
				output.Add(start.ToString());
			}
			else{
				output.Add(start.ToString() + "->" + prev.ToString());
			}
			
			if(i == nums.Length){
				break;
			}
			
			start = nums[i];
			prev = nums[i];
		}
		else{
			prev = nums[i];
			i++;
		}
	}
	
	return output;
}
```
