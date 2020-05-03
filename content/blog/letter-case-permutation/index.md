---
title: Letter Case Permutation
date: "2020-05-03"
type: problem-solving
description: Letter Case Permutation
tags: csharp
---

Note: This problem was taken from LeetCode - [Letter Case Permutation](https://leetcode.com/problems/letter-case-permutation/)

### Breadth First Approach

```csharp
public IList<string> LetterCasePermutation(string S) {
	Queue<char[]> bfsQueue = new Queue<char[]>();
	bfsQueue.Enqueue(new char[S.Length]);
	
	for(int i = 0; i < S.Length; i++){
		int count = bfsQueue.Count;
		
		for(int j = 0; j < count; j++){
			char[] temp = bfsQueue.Dequeue();

			if(Char.IsDigit(S[i])){    
				temp[i] = S[i];
				bfsQueue.Enqueue(temp);   
			}
			else{
				temp[i] = Char.ToLower(S[i]);
				bfsQueue.Enqueue(temp);
				
				char[] temp2 = (char[])temp.Clone();
				temp2[i] = Char.ToUpper(S[i]);
				bfsQueue.Enqueue(temp2);
			}
		}
	}
	
	List<string> output = new List<string>();
	
	while(bfsQueue.Count > 0){
		output.Add(new string(bfsQueue.Dequeue()));
	}
	
	return output;
}
```

### Recursion (Depth First Approach)

```csharp
public IList<string> LetterCasePermutation(string S) {
	List<string> output = new List<string>();
	
	this.LetterPerms(S, output, 0, new char[S.Length]);
	
	return output;
}

public void LetterPerms(string S, List<string> output, int currIndex, char[] constructed){
	if(currIndex > S.Length){
		return;
	}
	
	if(currIndex == S.Length){
		output.Add(new string(constructed));
		return;
	}
	
	if(Char.IsDigit(S[currIndex])){
		constructed[currIndex] = S[currIndex];
		this.LetterPerms(S, output, currIndex + 1, constructed);
	}
	else{
		constructed[currIndex] = Char.ToUpper(S[currIndex]);
		this.LetterPerms(S, output, currIndex + 1, constructed);
		constructed[currIndex] = Char.ToLower(S[currIndex]);
		this.LetterPerms(S, output, currIndex + 1, constructed);
	}
	
	return;
}
```
