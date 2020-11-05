---
title: Asteroid Collision
date: "2020-11-05"
type: problem-solving
description: Asteroid Collision
tags: csharp
---

Note: This problem was taken from LeetCode - [Asteroid Collision](https://leetcode.com/problems/asteroid-collision/)

### Using Stack

```csharp
public int[] AsteroidCollision(int[] asteroids) {
	Stack<int> st = new Stack<int>();
	
	foreach(int curr in asteroids){
		if(curr > 0){
			st.Push(curr);
		}
		else{
			while(st.Count > 0 && st.Peek() > 0 && st.Peek() < -curr){
				st.Pop();
			}
			
			if(st.Count > 0 && st.Peek() == -curr){
				st.Pop();
			}
			else if(st.Count == 0 || st.Peek() < 0){
				st.Push(curr);
			}
			
		}
	}
	
	int[] result = (int[])st.ToArray();
	Array.Reverse(result);
	
	return result;
}
```
