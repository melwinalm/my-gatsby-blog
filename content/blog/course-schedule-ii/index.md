---
title: Course Schedule II
date: "2020-07-18"
type: problem-solving
description: Course Schedule II
tags: csharp
---

Note: This problem was taken from LeetCode - [Course Schedule II](https://leetcode.com/problems/course-schedule-ii/)

### Topological Sorting using Kahn's Algorithm

```csharp
public int[] FindOrder(int numCourses, int[][] prerequisites) {
	List<HashSet<int>> map =  new List<HashSet<int>>();
	int[] inDegrees = new int[numCourses]; // This array will have the prerequisite count of all the courses
	
	for(int i = 0; i < numCourses; i++){
		map.Add(new HashSet<int>());
	}
	
	foreach(int[] item in prerequisites){
		int course = item[0];
		int depend = item[1];
		inDegrees[course]++;
		
		map[depend].Add(course);
	}
	
	Queue<int> bfsQueue = new Queue<int>();
	
	// The order of courses can be started from courses where the inDegrees count is 0
	for(int i = 0; i < numCourses; i++){
		if(inDegrees[i] == 0){
			bfsQueue.Enqueue(i);
		}
	}
	
	List<int> output = new List<int>();
	
	while(bfsQueue.Count > 0){
		int from = bfsQueue.Dequeue();
		
		output.Add(from);
		
		foreach(int to in map[from]){
			// Only add the course to the queue which have 0 in-degree count. 
			// Reduce the count each time that course is taken
			inDegrees[to]--;
			if(inDegrees[to] == 0){
				bfsQueue.Enqueue(to);
			}
		}
		
	}
	
	return output.Count == numCourses ? output.ToArray() : new int[0];
}
```
