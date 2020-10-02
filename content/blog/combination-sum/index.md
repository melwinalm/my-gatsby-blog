---
title: Combination Sum
date: "2020-10-02"
type: problem-solving
description: Combination Sum
tags: csharp
---

Note: This problem was taken from LeetCode - [Combination Sum](https://leetcode.com/problems/combination-sum/)

### Using Backtracking

```csharp
public IList<IList<int>> CombinationSum(int[] candidates, int target) {
	IList<IList<int>> output = new List<IList<int>>();
	
	Array.Sort(candidates);
	
	this.Combis(output, candidates, 0, target, new List<int>());
	
	return output;
}

public void Combis(IList<IList<int>> output, int[] candidates, int start, int target, List<int> tempList){
	if(target < 0){
		return;
	}
	else if(target == 0){
		List<int> temp = new List<int>();
		temp.AddRange(tempList);
		output.Add(temp);
	}
	else{
		for(int i = start; i < candidates.Length; i++){
			tempList.Add(candidates[i]);
			this.Combis(output, candidates, i, target - candidates[i], tempList);
			tempList.RemoveAt(tempList.Count - 1);
		}
	}
	
}
```
