---
title: Build an Array With Stack Operations
date: "2020-05-10"
type: problem-solving
description: Build an Array With Stack Operations
tags: csharp
---

Note: This problem was taken from LeetCode - [Build an Array With Stack Operations](https://leetcode.com/problems/build-an-array-with-stack-operations/)

### Using Linear Scan

```csharp
public IList<string> BuildArray(int[] target, int n) {
	List<string> output = new List<string>();
	int index = 0;
	
	for(int i = 1; i <= n; i++){
		if(index >= target.Length){
			break;
		}
		else if(target[index] == i){
			output.Add("Push");
			index++;
		}
		else{
			output.Add("Push");
			output.Add("Pop");
		}
	}
	
	return output;
}
```
