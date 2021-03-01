---
title: Maximum Frequency Stack
date: "2021-03-01"
type: problem-solvingMaximum Frequency StackScore of Parentheses
tags: csharp
---

Note: This problem was taken from LeetCode - [Maximum Frequency Stack](https://leetcode.com/problems/maximum-frequency-stack/)

### Using Dictionary with Stack

```csharp
Dictionary<int,int> freq;
Dictionary<int,Stack<int>> groupFreq;
int maxFreq;

public FreqStack() {
	freq = new Dictionary<int,int>();
	groupFreq = new Dictionary<int, Stack<int>>();
	maxFreq = 0;
}

public void Push(int x) {
	if(freq.ContainsKey(x)){
		freq[x]++;
	}
	else{
		freq[x] = 1;
	}
	
	if(freq[x] > maxFreq){
		maxFreq = freq[x];
	}
	
	if(groupFreq.ContainsKey(freq[x])){
		groupFreq[freq[x]].Push(x);
	}
	else{
		groupFreq[freq[x]] = new Stack<int>();
		groupFreq[freq[x]].Push(x);
	}
}

public int Pop() {
	if(groupFreq.ContainsKey(maxFreq)){
		int x = groupFreq[maxFreq].Pop();
		freq[x]--;
		if(groupFreq[maxFreq].Count == 0){
			maxFreq--;
		}
		return x;
	}
	
	return -1;
}
```
