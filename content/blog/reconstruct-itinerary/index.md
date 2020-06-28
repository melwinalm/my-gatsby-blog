---
title: Reconstruct Itinerary
date: "2020-06-28"
type: problem-solving
description: Reconstruct Itinerary
tags: csharp
---

Note: This problem was taken from LeetCode - [Reconstruct Itinerary](https://leetcode.com/problems/reconstruct-itinerary/)

### Using Depth First Search

```csharp
public IList<string> FindItinerary(IList<IList<string>> tickets) {
	Dictionary<string, List<string>> map = new Dictionary<string, List<string>>();
	List<string> output = new List<string>();
	
	// Storing the tickets in an adjacency list
	foreach(List<string> item in tickets){
		if(!map.ContainsKey(item[0])){
			map[item[0]] = new List<string>();
		}
		
		map[item[0]].Add(item[1]);
	}
	
	// Sorting the values in lexicographical order
	foreach(List<string> item in map.Values){
		item.Sort();
	}
	
	int totalTickets = tickets.Count;
	
	output.Add("JFK");
	this.DFS(map, "JFK", output, totalTickets, 0);
	
	return output;
}

public bool DFS(Dictionary<string, List<string>> map, string cur, List<string> output, int totalTickets, int usedTickets){
	if(!map.ContainsKey(cur)){
		return false;
	}
	
	List<string> tempList = map[cur];
	
	for(int i = 0; i < tempList.Count; i++){
		string tempPath = tempList[i];
		tempList.RemoveAt(i);
		output.Add(tempPath);
		
		usedTickets++;
		
		bool flag = this.DFS(map, tempPath, output, totalTickets, usedTickets);
		
		if(flag){
			return true;
		}
		
		if(totalTickets == usedTickets){
			return true;
		}
		
		// Backtracking
		tempList.Insert(i, tempPath);
		output.RemoveAt(output.Count - 1); // Remove the last element from the path
		
		usedTickets--;
	}
	
	return false;
}
```
