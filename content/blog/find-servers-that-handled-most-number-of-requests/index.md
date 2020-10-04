---
title: Find Servers That Handled Most Number of Requests
date: "2020-10-04"
type: problem-solving
description: Find Servers That Handled Most Number of Requests
tags: csharp
---

Note: This problem was taken from LeetCode - [Find Servers That Handled Most Number of Requests](https://leetcode.com/problems/find-servers-that-handled-most-number-of-requests/)

### Naive Approach

```csharp
public IList<int> BusiestServers(int k, int[] arrival, int[] load) {
	int[] busyCount = new int[k];
	
	int[] busyTill = new int[k];
	
	for(int i = 0; i < arrival.Length; i++){
		
		for(int j = 0; j < k; j++){
			if(arrival[i] >= busyTill[(i%k + j)%k]){
				busyTill[(i%k + j)%k] = arrival[i] + load[i];
				busyCount[(i%k + j)%k]++;
				break;
			}
		}
		
	}
	
	int maxSoFar = 0;
	
	foreach(int item in busyCount){
		maxSoFar = Math.Max(maxSoFar, item);
	}

	List<int> output = new List<int>();

	for(int i = 0; i < busyCount.Length; i++){
		if(busyCount[i] == maxSoFar){
			output.Add(i);
		}
	}
	
	return output;
}
```

### Using Priority Queue

To Be Solved
