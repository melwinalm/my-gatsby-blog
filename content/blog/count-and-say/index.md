---
title: Count and Say
date: "2020-05-22"
type: problem-solving
description: Count and Say
tags: csharp
---

Note: This problem was taken from LeetCode - [Count and Say](https://leetcode.com/problems/count-and-say/)

### Using Iteration

```csharp
public string CountAndSay(int n) {
	if(n <= 0){
		return "-1";    
	}
	
	string output = "1";
	
	for(int i = 1; i < n; i++){
		output = this.Builder(output);
	}
	
	return output;
}

public string Builder(string input){
	StringBuilder output = new StringBuilder();
	
	int i = 1;
	int count = 1;
	
	while(i < input.Length){
		if(input[i-1] == input[i]){
			count++;
		}
		else{
			output.Append(count.ToString() + input[i-1]);
			count = 1;
		}
		i++;            
	}
	
	output.Append(count.ToString() + input[i-1]);
	
	return output.ToString();
}
```
