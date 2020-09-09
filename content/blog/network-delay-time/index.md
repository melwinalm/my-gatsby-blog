---
title: Network Delay Time
date: "2020-09-08"
type: problem-solving
description: Network Delay Time
tags: csharp
---

Note: This problem was taken from LeetCode - [Network Delay Time](https://leetcode.com/problems/network-delay-time/)

### Using Floyd-Warshall Algorithm (N^3 time complexity, N^2 space complexity)

```csharp
public int NetworkDelayTime(int[][] times, int N, int K) {
	int[,] memo = new int[N+1,N+1];
	
	// Set the max value of all the edges to infinity
	for(int i = 1; i <= N; i++){
		for(int j = 1; j <=N; j++){
			memo[i,j] = Int32.MaxValue;
		}
	}
	
	// Update the edge weights
	foreach(int[] edge in times){
		int f = edge[0];
		int t = edge[1];
		int w = edge[2];
		
		memo[f,t] = w;
	}
	
	for(int i = 1; i <= N; i++){
		for(int j = 1; j <= N; j++){
			for(int k = 1; k <= N; k++){
				if(memo[j,i] != Int32.MaxValue && memo[i,k] != Int32.MaxValue){
					memo[j,k] = Math.Min(memo[j,k], memo[j,i] + memo[i,k]);
				}
			}
		}
	}
	
	int maxTime = 0;
	
	// Finding out the max time to reach all the nodes
	for(int i = 1; i <= N; i++){
		if(i == K){
			continue;
		}
		
		// validate if there's any path from K to other nodes. If the weight is infinity then it means there's no path.
		if(memo[K, i] == Int32.MaxValue){
			return -1;
		}
		else{
			maxTime = Math.Max(maxTime, memo[K,i]);
		}
		
	}
	
	return maxTime;
}
```

### Bellman-Ford Algorithm (VE time complexity, V space complexity)

```csharp
public int NetworkDelayTime(int[][] times, int N, int K) {
	Dictionary<int, List<Tuple<int,int>>> graph = new Dictionary<int, List<Tuple<int,int>>>();
	
	// Initialize the graph
	for(int i = 1; i <= N; i++){
		graph[i] = new List<Tuple<int,int>>();
	}
	
	// Build the graph
	foreach(int[] edge in times){
		int f = edge[0];
		int t = edge[1];
		int w = edge[2];
		
		graph[f].Add(new Tuple<int,int>(t,w));
	}
	
	Queue<Node> bfsQueue = new Queue<Node>();
	bfsQueue.Enqueue(new Node(K, 0));
	
	int[] dist = new int[N+1]; // this array holds the smallest distance to a node from K 
	Array.Fill(dist, 101);
	dist[K] = 0; // Distance from start node to start node is 0
	
	while(bfsQueue.Count > 0){
		Node tempNode = bfsQueue.Dequeue();
		int currNode = tempNode.node;
		int currWeight = tempNode.weight;
		
		foreach(var edge in graph[currNode]){
			if(dist[edge.Item1] > currWeight + edge.Item2){
				dist[edge.Item1] = currWeight + edge.Item2;
				bfsQueue.Enqueue(new Node(edge.Item1, dist[edge.Item1]));
			}
		}
	}

	// Finding the max time
	int maxTime = 0;
	for(int i = 1; i <= N; i++){
		if(dist[i] == 101){
			return -1;
		}
		else{
			maxTime = Math.Max(maxTime, dist[i]);
		}
	}
	
	return maxTime;
}
```

### Dijkstra's Algorithm (Using Min Heaps) (VElogV time complexity)

Changes compared to Bellman-Ford algorithm are
- Instead of a Queue, Priority Queue with Min Heaps is used.
- visited array is used track the nodes which are visited.

```csharp
public int NetworkDelayTime(int[][] times, int N, int K) {
	Dictionary<int, List<Tuple<int,int>>> graph = new Dictionary<int, List<Tuple<int,int>>>();
	
	// Initialize the graph
	for(int i = 1; i <= N; i++){
		graph[i] = new List<Tuple<int,int>>();
	}
	
	// Build the graph
	foreach(int[] edge in times){
		int f = edge[0];
		int t = edge[1];
		int w = edge[2];
		
		graph[f].Add(new Tuple<int,int>(t,w));
	}
	
	PriorityQueue<Node> pq = new PriorityQueue<Node>();
	pq.Enqueue(0, new Node(K, 0));
	
	int[] dist = new int[N+1]; // this array holds the smallest distance to a node from K
	bool[] visited = new bool[N+1];
	Array.Fill(dist, 101);
	dist[K] = 0; // Distance from start node to start node is 0
	
	while(pq.Count > 0){
		Node tempNode = pq.Dequeue();
		int currNode = tempNode.node;
		int currWeight = tempNode.weight;
		
		if(visited[currNode]){
			continue;
		}
		
		visited[currNode] = true;
		
		foreach(var edge in graph[currNode]){
			if(dist[edge.Item1] > currWeight + edge.Item2){
				dist[edge.Item1] = currWeight + edge.Item2;
				pq.Enqueue(dist[edge.Item1], new Node(edge.Item1, dist[edge.Item1]));
			}
		}
	}

	// Finding the max time
	int maxTime = 0;
	for(int i = 1; i <= N; i++){
		if(dist[i] == 101){
			return -1;
		}
		else{
			maxTime = Math.Max(maxTime, dist[i]);
		}
	}
	
	return maxTime;
}
```
