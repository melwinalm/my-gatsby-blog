---
title: Kids With the Greatest Number of Candies
date: "2020-05-03"
type: problem-solving
description: Kids With the Greatest Number of Candies
tags: csharp
---

Note: This problem was taken from LeetCode - [Kids With the Greatest Number of Candies](https://leetcode.com/problems/kids-with-the-greatest-number-of-candies/)

### Solution

```csharp
public IList<bool> KidsWithCandies(int[] candies, int extraCandies) {
	int max = Int32.MinValue;
	
	for(int i = 0; i < candies.Length; i++){
		max = Math.Max(max, candies[i]);
	}
	
	List<bool> output = new List<bool>();
	
	for(int i = 0; i < candies.Length; i++){
		if(extraCandies + candies[i] >= max){
			output.Add(true);
		}
		else{
			output.Add(false);
		}
	}
	
	return output;
}
```
