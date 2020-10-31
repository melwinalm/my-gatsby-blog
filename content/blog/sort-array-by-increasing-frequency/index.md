---
title: Sort Array by Increasing Frequency
date: "2020-10-31"
type: problem-solving
description: Sort Array by Increasing Frequency
tags: csharp
---

Note: This problem was taken from LeetCode - [Sort Array by Increasing Frequency](https://leetcode.com/problems/sort-array-by-increasing-frequency/)

### Using Sorting with Dictionary

```csharp
public int[] FrequencySort(int[] nums) {
	Dictionary<int,int> freq = new Dictionary<int,int>();
	
	foreach(int num in nums){
		if(!freq.ContainsKey(num)){
			freq[num] = 0;
		}
		
		freq[num]++;
	}
	
	Tuple<int,int>[] freqCount = new Tuple<int,int>[freq.Count];
	
	int i = 0;
	
	foreach(var item in freq){
		freqCount[i] = new Tuple<int,int>(item.Key,item.Value);
		i++;
	}
	
	Array.Sort(freqCount, (a,b) => a.Item2 == b.Item2 ? b.Item1 - a.Item1 : a.Item2 - b.Item2);
	
	int[] output = new int[nums.Length];
	i = 0;
	foreach(var item in freqCount){
		int num = item.Item1;
		int count = item.Item2;
		
		while(count != 0){
			output[i] = num;
			count--;
			i++;
		}
	}
	
	return output;        
}
```
