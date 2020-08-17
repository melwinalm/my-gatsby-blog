---
title: Distribute Candies to People
date: "2020-08-17"
type: problem-solving
description: Distribute Candies to People
tags: csharp
---

Note: This problem was taken from LeetCode - [Distribute Candies to People](https://leetcode.com/problems/distribute-candies-to-people/)

### Intuitive Approach

```csharp
public int[] DistributeCandies(int candies, int num_people) {
	int[] output = new int[num_people];
	
	int size = 1;
	int index = 0;
	while(candies >= size){
		output[index] += size;
		candies -= size;
		size++;
		index++;
		
		if(index == num_people){
			index = 0;
		}
	}
	
	output[index] += candies;
	
	return output;
}
```
