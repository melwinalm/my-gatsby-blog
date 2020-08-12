---
title: Pascal's Triangle II
date: "2020-08-12"
type: problem-solving
description: Pascal's Triangle II
tags: csharp
---

Note: This problem was taken from LeetCode - [Pascal's Triangle II](https://leetcode.com/problems/pascals-triangle-ii/)

```csharp
public IList<int> GetRow(int rowIndex) {
	if(rowIndex < 1){
		return new int[]{1};
	}
	
	int[] output = new int[rowIndex+1];
	int[] temp = new int[rowIndex+1];
	
	output[0] = 1;
	output[1] = 1;
	
	for(int i = 1; i < rowIndex; i++){
		int index = 0;
		int maxIndex = i;
		Array.Copy(output, temp, rowIndex+1);

		output[0] = 1;
		output[maxIndex+1] = 1;
		
		while(maxIndex > 0){
			output[maxIndex] = temp[maxIndex] + temp[maxIndex-1];
			maxIndex--;
		}
	}
	
	return output.ToList();
}
```
