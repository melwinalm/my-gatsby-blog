---
title: Sequential Digits
date: "2020-09-19"
type: problem-solving
description: Sequential Digits
tags: csharp
---

Note: This problem was taken from LeetCode - [Sequential Digits](https://leetcode.com/problems/sequential-digits/)

### Using Queue

```csharp
public IList<int> SequentialDigits(int low, int high) {
	List<int> output = new List<int>();
	
	Queue<int> que = new Queue<int>();
	
	for(int i = 1; i <= 9; i++){
		que.Enqueue(i);            
	}
	
	while(que.Count > 0){
		int currNum = que.Dequeue();
		
		if(currNum >= low && currNum <= high){
			output.Add(currNum);
		}
		
		int lastDigit = currNum % 10;
		int newNum = currNum * 10 + lastDigit + 1;
		
		if(lastDigit < 9 && newNum <= high){
			que.Enqueue(newNum);
		}
	}
	
	return output;
}
```
