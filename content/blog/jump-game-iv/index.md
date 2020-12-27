---
title: Jump Game IV
date: "2020-12-27"
type: problem-solving
description: Jump Game IV
---

Note: This problem was taken from LeetCode - [Jump Game IV](https://leetcode.com/problems/jump-game-iv/)

### Breadth First Search

```csharp
public int MinJumps(int[] arr) {
	Dictionary<int, List<int>> graph = new Dictionary<int, List<int>>();
	
	for(int i = arr.Length - 1; i >= 0; i--){
		int x = arr[i];
		if(!graph.ContainsKey(x)){
			graph[x] = new List<int>();
		}
		graph[x].Add(i);
	}
	
	bool[] visited = new bool[arr.Length];
	
	Queue<int> bfsQueue = new Queue<int>();
	bfsQueue.Enqueue(0);
	int depth = 0;
	
	while(bfsQueue.Count > 0){
		int count = bfsQueue.Count;
		
		for(int i = 0; i < count; i++){
			int temp = bfsQueue.Dequeue();
			
			if(temp == arr.Length - 1){
				return depth;
			}
			
			if(visited[temp] == true){
				continue;
			}
			
			visited[temp] = true;
			
			List<int> next = graph[arr[temp]];
			
			if(temp - 1 >= 0){
				next.Add(temp - 1);
			}
			
			if(temp + 1 < arr.Length){
				next.Add(temp + 1);
			}
			
			foreach(int item in graph[arr[temp]]){
				bfsQueue.Enqueue(item);
			}
			next.Clear();
		}
		
		depth++;
	}
	
	return arr.Length - 1;
}
```
