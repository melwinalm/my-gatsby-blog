---
title: Course Schedule
date: "2020-05-29"
type: problem-solving
description: Course Schedule
tags: csharp
---

Note: This problem was taken from LeetCode - [Course Schedule](https://leetcode.com/problems/course-schedule/)

### Using DFS

```csharp
public bool CanFinish(int numCourses, int[][] prerequisites)
{
	Dictionary<int, List<int>> map = new Dictionary<int, List<int>>();
	
	// Initialising the adjacency list
	for (int i = 0; i < numCourses; i++)
	{
		map[i] = new List<int>();
	}
	
	// Adding all the courses and it's prerequisites to the dictionary
	foreach (int[] item in prerequisites)
	{
		map[item[0]].Add(item[1]);
	}

	HashSet<int> track = new HashSet<int>();

	foreach (var item in map)
	{
		bool flag = this.DFS(map, track, item.Key);

		if (flag == false)
		{
			return false;
		}
	}

	return true;
}

public bool DFS(Dictionary<int, List<int>> map, HashSet<int> track, int courseId)
{
	// If the course id already exists then return false, since there is a circular dependency of courses
	if (track.Contains(courseId))
	{
		return false;
	}

	track.Add(courseId);
	
	// Recursively call the DFS function on all prerequisites of course.
	foreach (int item in map[courseId])
	{
		bool flag = this.DFS(map, track, item);

		if (flag == false)
		{
			return false;
		}
	}
	
	// Remove te course id from the HaseSet to backtrack
	track.Remove(courseId);

	return true;
}  
```
