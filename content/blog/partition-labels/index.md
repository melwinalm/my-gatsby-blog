---
title: Partition Labels
date: "2020-09-05"
type: problem-solving
description: Partition Labels
tags: csharp
---

Note: This problem was taken from LeetCode - [Partition Labels](https://leetcode.com/problems/partition-labels/)

### Using Greedy Approach

```csharp
public IList<int> PartitionLabels(string S) {
	int[] last = new int[26];
	
	for(int i = 0 ; i < S.Length; i++){
		last[S[i] - 'a'] = i;
	}
	
	List<int> output = new List<int>();
	
	int lastAppear = 0; // Stores the maximum index that can fit into the group for a given i;
	int subStart = 0;   // Stores the index of the start of the sug group
	for(int i = 0; i < S.Length; i++){
		lastAppear = Math.Max(lastAppear, last[S[i] - 'a']);
		
		if(i == lastAppear){
			output.Add(lastAppear - subStart + 1);
			subStart = lastAppear + 1;
		}
	}
	
	return output;
}
```
