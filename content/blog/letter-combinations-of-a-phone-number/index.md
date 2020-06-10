---
title: Letter Combinations of a Phone Number
date: "2020-06-10"
type: problem-solving
description: Letter Combinations of a Phone Number
tags: csharp
---

Note: This problem was taken from LeetCode - [Letter Combinations of a Phone Number](https://leetcode.com/problems/letter-combinations-of-a-phone-number/)

### Using Recursive Approach

```csharp
public IList<string> LetterCombinations(string digits) {
	List<string> output = new List<string>();
	
	if(digits.Length == 0){
		return output;
	}
	
	Dictionary<int, string> map = new Dictionary<int, string>();
	map[2] = "abc";
	map[3] = "def";
	map[4] = "ghi";
	map[5] = "jkl";
	map[6] = "mno";
	map[7] = "pqrs";
	map[8] = "tuv";
	map[9] = "wxyz";
	
	this.Combinations(digits, 0, "", map, output);

	return output;
}

public void Combinations(string digits, int currIndex, string comb, Dictionary<int, string> map, List<string> output){
	if(currIndex == digits.Length){
		output.Add(comb);
		return;
	}
	
	string combns = map[Convert.ToInt32(digits[currIndex] - '0')];
	
	foreach(char c in combns){
		this.Combinations(digits, currIndex + 1, comb + c, map, output);
	}
}
```
