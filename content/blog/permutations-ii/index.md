---
title: Permutations II
date: "2020-11-13"
type: problem-solving
description: Permutations II
tags: csharp
---

Note: This problem was taken from LeetCode - [Permutations II](https://leetcode.com/problems/permutations-ii/)

### Using Recursion

```csharp
public IList<IList<int>> PermuteUnique(int[] nums) {
	IList<IList<int>> output = new List<IList<int>>();
	
	int N = nums.Length;
	
	bool[] visited = new bool[N];
	Array.Sort(nums);
	this.DFS(nums, visited, new List<int>(), output);
	
	return output;
}

public void DFS(int[] nums, bool[] visited, List<int> temp, IList<IList<int>> output){
	if(temp.Count == nums.Length){
		List<int> tempList = new List<int>();
		tempList.AddRange(temp);
		output.Add(tempList);
	}
	
	for(int i = 0; i < nums.Length; i++){
		if(visited[i]){
			continue;
		}
		
		if(i > 0 && nums[i] == nums[i-1] && !visited[i-1]){
			continue;
		}
		
		visited[i] = true;
		temp.Add(nums[i]);
		this.DFS(nums, visited, temp, output);
		temp.RemoveAt(temp.Count - 1);
		visited[i] = false;
	}
	
}
```
