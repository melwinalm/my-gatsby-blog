---
title: Pancake Sorting
date: "2020-08-29"
type: problem-solving
description: Pancake Sorting
tags: csharp
---

Note: This problem was taken from LeetCode - [Pancake Sorting](https://leetcode.com/problems/pancake-sorting/)

### Intuitive Approach

```csharp
public IList<int> PancakeSort(int[] A) {
	List<int> output = new List<int>();
	
	for(int i = A.Length; i > 0; i--){
		int currIndex = this.Find(A, i);
		
		// If the current number is in the current position then it need not be flipped
		if(currIndex == i-1){
			continue;
		}
		
		this.Flip(A, currIndex);
		this.Flip(A, i-1);
		
		output.Add(currIndex+1);
		output.Add(i);
	}
	
	return output;
}

public int Find(int[] A, int num){
	for(int i = 0; i < A.Length; i++){
		if(A[i] == num){
			return i;
		}
	}
	
	return -1;
}

public void Flip(int[] A, int eIndex){
	int sIndex = 0;
	
	while(sIndex < eIndex){
		int temp = A[sIndex];
		A[sIndex] = A[eIndex];
		A[eIndex] = temp;
		sIndex++;
		eIndex--;
	}
}
```
