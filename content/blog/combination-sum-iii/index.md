---
title: Combination Sum III
date: "2020-09-12"
type: problem-solving
description: Combination Sum III
tags: csharp
---

Note: This problem was taken from LeetCode - [Combination Sum III](https://leetcode.com/problems/combination-sum-iii/)

### Using Backtracking

```csharp
public IList<IList<int>> CombinationSum3(int k, int n) {
	IList<IList<int>> output = new List<IList<int>>();
	
	this.Combinations(output, new List<int>(), 1, k, n);
	
	return output;
}

public void Combinations(IList<IList<int>> output, List<int> tempOutput, int currIndex, int remSize, int remSum){
	if(remSize == 0 && remSum == 0){
		List<int> temp = new List<int>();
		temp.AddRange(tempOutput);
		
		output.Add(temp);
		return;
	}
	
	for(int i = currIndex; i <= 9; i++){
		tempOutput.Add(i);
		this.Combinations(output, tempOutput, i+1, remSize-1, remSum-i);
		tempOutput.RemoveAt(tempOutput.Count - 1);
	}        
}
```

### Using Backtracking (Improved Version)

```csharp
public IList<IList<int>> CombinationSum3(int k, int n) {
	IList<IList<int>> output = new List<IList<int>>();
	
	this.Combinations(output, new List<int>(), 1, k, n);
	
	return output;
}

public void Combinations(IList<IList<int>> output, List<int> tempOutput, int currIndex, int remSize, int remSum){
	if(remSize < 0){
		return;
	}
	
	if(remSize == 0 && remSum == 0){
		List<int> temp = new List<int>();
		temp.AddRange(tempOutput);
		
		output.Add(temp);
		return;
	}
	
	for(int i = currIndex; i <= 9; i++){
		if(remSum - i < 0){
			continue;
		}
		
		tempOutput.Add(i);
		this.Combinations(output, tempOutput, i+1, remSize-1, remSum-i);
		tempOutput.RemoveAt(tempOutput.Count - 1);
	}        
}
```
