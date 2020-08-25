---
title: Boats to Save People
date: "2020-08-25"
type: problem-solving
description: Boats to Save People
tags: csharp
---

Note: This problem was taken from LeetCode - [Boats to Save People](https://leetcode.com/problems/boats-to-save-people/)

### Naive Approach

```csharp
public int NumRescueBoats(int[] people, int limit) {
	Dictionary<int,int> map = new Dictionary<int,int>();
	
	foreach(int item in people){
		if(!map.ContainsKey(item)){
			map[item] = 0;
		}
		
		map[item] += 1;
	}

	HashSet<int> indices = new HashSet<int>();
	
	for(int j = 0; j < people.Length; j++){
		indices.Add(j);
	}
	
	int count = 0;
	
	int i = 0;
	while(indices.Count > 0){
		if(!indices.Contains(i)){
			i++;
			continue;
		}
		
		int weight = people[i];
		indices.Remove(i);
		
		int maxWeight = -1;
		int maxWeightIndex = -1;
		
		foreach(var index in indices){
			if(weight + people[index] == limit){
				maxWeight = people[index];
				maxWeightIndex = index;
				break;
			}
			else if(weight + people[index] <= limit && people[index] > maxWeight){
				maxWeight = people[index];
				maxWeightIndex = index;
			}
		}
		
		count++;
		i++;
		if(maxWeightIndex != -1){
			indices.Remove(maxWeightIndex);
		}
		
	}
	
	return count;
}
```

### Greedy Approach (Two Pointer Solution)

```csharp
public int NumRescueBoats(int[] people, int limit) {
	Array.Sort(people);
	
	int sIndex = 0;
	int eIndex = people.Length - 1;
	
	int count = 0;
	
	while(sIndex <= eIndex){
		if(people[sIndex] + people[eIndex] <= limit){
			count++;
			sIndex++;
			eIndex--;
		}
		else{
			count++;
			eIndex--;
		}
		
	}
	
	return count;
}
```
