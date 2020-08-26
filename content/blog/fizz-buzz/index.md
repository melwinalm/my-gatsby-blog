---
title: Fizz Buzz
date: "2020-08-26"
type: problem-solving
description: Fizz Buzz
tags: csharp
---

Note: This problem was taken from LeetCode - [Fizz Buzz](https://leetcode.com/problems/fizz-buzz/)

### Naive Solution

```csharp
public IList<string> FizzBuzz(int n) {
	List<string> output = new List<string>();
	
	for(int i = 1; i <= n; i++){
		if(i % 5 == 0 && i % 3 == 0){
			output.Add("FizzBuzz");
		}
		else if(i % 3 == 0){
			output.Add("Fizz");
		}
		else if(i % 5 == 0){
			output.Add("Buzz");
		}
		else{
			output.Add(i.ToString());
		}
	}
	
	return output;
}
```
