---
title: Max Difference You Can Get From Changing an Integer
date: "2020-05-03"
type: problem-solving
description: Max Difference You Can Get From Changing an Integer
tags: csharp
---

Note: This problem was taken from LeetCode - [Max Difference You Can Get From Changing an Integer](https://leetcode.com/problems/max-difference-you-can-get-from-changing-an-integer/)

### Solution

```csharp
public int MaxDiff(int num) {
	string inp = num.ToString();
	
	char[] options = new char[]{'0','1','2','3','4','5','6','7','8','9'};
	
	int max = Int32.MinValue;
	
	for(int i = 0; i < inp.Length; i++){
		for(int j = 0; j < options.Length; j++){
			max = Math.Max(max, Int32.Parse(inp.Replace(inp[i], options[j])));
		}
	}
	
	int min = Int32.MaxValue;
	
	for(int i = 0; i < inp.Length; i++){
		for(int j = 0; j < options.Length; j++){
			
			int temp = Int32.Parse(inp.Replace(inp[i], options[j]));
			
			// This condition will check if the number has any preceding zeroes
			// It will check if the number is not 0
			if(temp.ToString().Length == inp.Length && temp != 0){
				min = Math.Min(min, temp);    
			}
		}
	}
	return max - min;
}
```
