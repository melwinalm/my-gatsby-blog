---
title: Keys and Rooms
date: "2021-03-19"
type: problem-solving
description: Keys and Rooms
tags: csharp
---

Note: This problem was taken from LeetCode - [Keys and Rooms](https://leetcode.com/problems/keys-and-rooms/)

### Depth First Search

```csharp
public bool CanVisitAllRooms(IList<IList<int>> rooms) {
	HashSet<int> set = new HashSet<int>();
	set.Add(0);
	
	Stack<int> stack = new Stack<int>();
	stack.Push(0);
	
	while(stack.Count > 0){
		int room = stack.Pop();
		
		foreach(int item in rooms[room]){
			if(!set.Contains(item)){
				set.Add(item);
				stack.Push(item);
			}
		}
	}
	
	return rooms.Count == set.Count;
}
```
