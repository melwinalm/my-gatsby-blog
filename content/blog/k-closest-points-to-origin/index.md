---
title: K Closest Points to Origin
date: "2020-05-10"
type: problem-solving
description: K Closest Points to Origin
tags: csharp
---

Note: This problem was taken from LeetCode - [K Closest Points to Origin](https://leetcode.com/problems/k-closest-points-to-origin/)

### Using Priority Queue (Min Heap)

##### Note: Priority Queue implementation can be found [here](/priority-queue-implementation/)

```csharp
public int[][] KClosest(int[][] points, int K) {
	List<int[]> output = new List<int[]>();
	
	PriorityQueue<int[]> pq = new PriorityQueue<int[]>();
	
	for(int i = 0; i < points.Length; i++){
		int distance = (int)(Math.Pow(points[i][0], 2) + Math.Pow(points[i][1], 2));
		pq.Enqueue(distance, points[i]);
	}

	for(int i = 0; i < K; i++){
		output.Add(pq.Dequeue());
	}
	
	return output.ToArray();
}
```
