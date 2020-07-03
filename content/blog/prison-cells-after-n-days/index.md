---
title: Prison Cells After N Days
date: "2020-07-03"
type: problem-solving
description: Prison Cells After N Days
tags: csharp
---

Note: This problem was taken from LeetCode - [Prison Cells After N Days](https://leetcode.com/problems/prison-cells-after-n-days/)

### Using HashSet

```csharp
public int[] PrisonAfterNDays(int[] cells, int N) {  
	int count = 0;
	HashSet<string> set = new HashSet<string>();
	
	bool hasCycle = false;
	
	for(int i = 0; i < N; i++){
		int[] next = this.NextDay(cells);
		
		string key = string.Concat(next);
		
		if(!set.Contains(key)){
			set.Add(key);
			count++;
		}
		else{
			hasCycle = true;
			break;
		}
		cells = next;
	}
	
	if(hasCycle){
		int n = N % count;
		
		for(int i = 0; i < n; i++){
			cells = this.NextDay(cells);
		}
		
	}

	return cells;
}

public int[] NextDay(int[] cells){
	int[] temp = new int[cells.Length];
	
	for(int i = 1; i < cells.Length - 1; i++){
		temp[i] = cells[i-1] == cells[i+1] ? 1 : 0;
	}
	
	return temp;
}
```
