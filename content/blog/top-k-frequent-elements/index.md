---
title: Top K Frequent Elements
date: "2020-05-01"
type: problem-solving
description: Top K Frequent Elements
tags: csharp
---

Note: This problem was taken from LeetCode - [Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/)

### Using Dictionary and Priority Queue

Iterate through the given array and store the count in a dictionary. Now enqueue all the values of the dictionary into a Priority Queue. Now dequeue the first K elements from the queue to get the top K frequent elements.

#### Note: Priority Queue Implementation can be found [here](/priority-queue-implementation-with-generics/)

```csharp
public int[] TopKFrequent(int[] nums, int k) {
	Dictionary<int,int> map = new Dictionary<int,int>();
	
	for(int i = 0; i < nums.Length; i++){
		if(map.ContainsKey(nums[i])){
			map[nums[i]] += 1;
		}
		else{
			map[nums[i]] = 1;
		}
	}
	
	PriorityQueue<int> pq = new PriorityQueue<int>();
	
	foreach(var item in map){
		pq.Enqueue(item.Value, item.Key);
	}
	
	int[] output = new int[k];
	
	for(int i = 0; i < k; i++){
		output[i] = pq.Dequeue();
	}
	
	return output;
}
```
