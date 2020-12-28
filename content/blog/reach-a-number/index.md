---
title: Reach a Number
date: "2020-12-28"
type: problem-solving
description: Reach a Number
---

Note: This problem was taken from LeetCode - [Reach a Number](https://leetcode.com/problems/reach-a-number/)

### Breadth First Search

```csharp
public int ReachNumber(int target) {
	if(target == 0){
		return 0;
	}
	
	int steps = 0;
	int currNum = 0;
	int stepSize = 0;
	
	Queue<int> bfsQueue = new Queue<int>();
	bfsQueue.Enqueue(0);
	
	while(true){
		int count = bfsQueue.Count;
		stepSize++;
		
		for(int i = 0; i < count; i++){
			int temp = bfsQueue.Dequeue();
			
			if(temp == target){
				return steps;
			}
			
			bfsQueue.Enqueue(temp + stepSize);
			bfsQueue.Enqueue(temp - stepSize);
		}
		steps++;
	}
	
	return steps;
}
```

### Greedy Approach

```csharp
public int ReachNumber(int target) {
	target = Math.Abs(target); // The steps of a target are regardless of the sign

	int steps = 0;
	int sum = 0;
	
	// Keep updating the sum until you reach the target number
	while(sum < target){
		steps++;
		sum += steps;
	}

	while((sum - target) % 2 != 0){
		steps++;
		sum += steps;
	}
	
	return steps;
}
```
