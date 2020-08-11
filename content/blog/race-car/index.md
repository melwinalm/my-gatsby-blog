---
title: Race Car
date: "2020-08-11"
type: problem-solving
description: Race Car
tags: csharp
---

Note: This problem was taken from LeetCode - [Race Car](https://leetcode.com/problems/race-car/)

### Breadth First Approach (Time Limit Exceeded Error)

```csharp
public int Racecar(int target) {
	int pos = 0;
	int speed = 1;
	
	int depth = 0;
	
	Queue<Tuple<int,int>> bfsQueue = new Queue<Tuple<int,int>>();
	bfsQueue.Enqueue(new Tuple<int,int>(pos, speed));
	
	while(bfsQueue.Count > 0){
		int count = bfsQueue.Count;
		
		for(int i = 0; i < count; i++){
			Tuple<int,int> temp = bfsQueue.Dequeue();
			
			int tempPos = temp.Item1;
			int tempSpeed = temp.Item2;
			
			if(tempPos == target){
				return depth;
			}
			
			bfsQueue.Enqueue(new Tuple<int,int>(tempPos+tempSpeed, tempSpeed*2));
			var A = new Tuple<int,int>(tempPos, -1);
			var R = new Tuple<int,int>(tempPos, 1);
			bfsQueue.Enqueue(tempSpeed >= 0 ? A : R);
		}
		depth++;
	}
	
	return depth;
}
```

### Breadth First Approach with Pruning (Time Limit Exceeded Error)

```csharp
public int Racecar(int target) {
	int pos = 0;
	int speed = 1;
	
	int depth = 0;
	
	Queue<string> bfsQueue = new Queue<string>();
	bfsQueue.Enqueue(pos + "$" + speed);
	
	HashSet<string> visited = new HashSet<string>();
	
	while(bfsQueue.Count > 0){
		int count = bfsQueue.Count;
		
		for(int i = 0; i < count; i++){
			string temp = bfsQueue.Dequeue();
			
			int tempPos = Convert.ToInt32(temp.Split("$")[0]);
			int tempSpeed = Convert.ToInt32(temp.Split("$")[1]);
			
			if(tempPos == target){
				return depth;
			}
			// Pruning 1 - Preveting duplication of efforts
			if(visited.Contains(tempPos + "$" + tempSpeed)){
				continue;
			}
			
			visited.Add(tempPos + "$" + tempSpeed);
			
			// Pruning 2 - Reducing the search boundary
			if(Math.Abs(tempPos + tempSpeed - target) < target){
				bfsQueue.Enqueue((tempPos+tempSpeed) + "$" + (tempSpeed*2));                    
			}
			
			if(Math.Abs(tempPos - target) < target){
				var A = tempPos + "$-1";
				var R = tempPos +  "$1";
				bfsQueue.Enqueue(tempSpeed >= 0 ? A : R);
			}
		}
		depth++;
	}
	
	return depth;
}
```
