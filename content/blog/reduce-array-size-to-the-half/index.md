---
title: Reduce Array Size to The Half
date: "2020-08-25"
type: problem-solving
description: Reduce Array Size to The Half
tags: csharp
---

Note: This problem was taken from LeetCode - [Reduce Array Size to The Half](https://leetcode.com/problems/reduce-array-size-to-the-half/)

### Greedy Approach

```csharp
public int MinSetSize(int[] arr) {
	Dictionary<int, int> freq = new Dictionary<int,int>();
	
	foreach(int item in arr){
		if(!freq.ContainsKey(item)){
			freq[item] = 0;
		}
		
		freq[item] += 1;
	}
	
	int[] counts = new int[freq.Count];
	
	int i = 0;
	foreach(var item in freq){
		counts[i] = item.Value;
		i++;
	}
	
	Array.Sort(counts, (a,b) => b-a);
	
	int reqWeight = arr.Length / 2;
	int count = 0;
	
	while(reqWeight > 0){
		reqWeight -= counts[count];
		count++;
	}
	
	return count;
 }
```
