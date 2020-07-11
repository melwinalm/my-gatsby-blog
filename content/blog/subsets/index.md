---
title: Subsets
date: "2020-07-11"
type: problem-solving
description: Subsets
tags: csharp
---

Note: This problem was taken from LeetCode - [Subsets](https://leetcode.com/problems/subsets/)

### Using DFS

```csharp
public IList<IList<int>> Subsets(int[] nums) {
	IList<IList<int>> output = new List<IList<int>>();
	
	this.Combinations(nums, 0, output, new List<int>());
	return output;
}

public void Combinations(int[] nums, int currIndex, IList<IList<int>> output, List<int> tempList){
	output.Add(new List<int>(tempList));
	
	for(int i = currIndex; i < nums.Length; i++){
		tempList.Add(nums[i]);
		this.Combinations(nums, i+1, output, tempList);
		tempList.RemoveAt(tempList.Count-1);
	}
}
```

### Using Iteration

Initially add the empty array to the output list. Next, iterate through all the numbers of the input array, and on each iteration, create a copy of all the items from the output list and add the number from the current iteration. See the below example.

#### Example 
input = [1, 2]

Initial: []

Iteration 1: [], [1]

Iteration 2: [], [1], [2], [1,2]

```csharp
public IList<IList<int>> Subsets(int[] nums) {
	IList<IList<int>> output = new List<IList<int>>();
	
	output.Add(new List<int>());
	
	for(int i = 0; i < nums.Length; i++){
		int outN = output.Count;
		
		for(int j = 0; j < outN; j++){
			List<int> subset = new List<int>(output[j]);
			subset.Add(nums[i]);
			output.Add(subset);
		}
		
	}
	
	return output;
}
```
