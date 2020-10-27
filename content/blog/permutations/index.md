---
title: Permutations
date: "2020-10-27"
type: problem-solving
description: Permutations
tags: csharp
---

Note: This problem was taken from LeetCode - [Permutations](https://leetcode.com/problems/permutations/)

### Using Backtracking

```csharp
public IList<IList<int>> Permute(int[] nums) {
	IList<IList<int>> output = new List<IList<int>>();
	
	List<int> tempList = new List<int>();
	
	this.Backtrack(output, nums, tempList);
	
	return output;
}

public void Backtrack(IList<IList<int>> output, int[] nums, List<int> tempList){
	if(tempList.Count == nums.Length){
		output.Add(new List<int>(tempList));
		return;
	}
	
	for(int i = 0; i < nums.Length; i++){
		if(tempList.Contains(nums[i])){
			continue;
		}

		tempList.Add(nums[i]);
		this.Backtrack(output, nums, tempList);
		tempList.RemoveAt(tempList.Count - 1);
	}
}
```

### Using Backtracking + HashSet (Time improved)

```csharp
public IList<IList<int>> Permute(int[] nums) {
	IList<IList<int>> output = new List<IList<int>>();
	
	List<int> tempList = new List<int>();
	HashSet<int> used = new HashSet<int>();
	
	this.Backtrack(output, nums, tempList, used);
	
	return output;
}

public void Backtrack(IList<IList<int>> output, int[] nums, List<int> tempList, HashSet<int> used){
	if(tempList.Count == nums.Length){
		output.Add(new List<int>(tempList));
		return;
	}
	
	for(int i = 0; i < nums.Length; i++){
		if(used.Contains(nums[i])){
			continue;
		}

		tempList.Add(nums[i]);
		used.Add(nums[i]);
		
		this.Backtrack(output, nums, tempList, used);
		
		tempList.RemoveAt(tempList.Count - 1);
		used.Remove(nums[i]);
	}
}
```
