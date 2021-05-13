---
title: Ambiguous Coordinates
date: "2021-05-13"
type: problem-solving
description: Ambiguous Coordinates
tags: csharp
---

Note: This problem was taken from LeetCode - [Ambiguous Coordinates](https://leetcode.com/problems/ambiguous-coordinates/)

### Using Brute Force Approach

```csharp
public IList<string> AmbiguousCoordinates(string s) {
	List<string> output = new List<string>();

	for(int i = 2; i < s.Length-1; i++){
	    foreach(string left in this.Helper(s, 1, i)){
		foreach(string right in this.Helper(s, i, s.Length-1)){
		    output.Add("(" + left + ", " + right + ")");
		}
	    }
	}

	return output;
}

public List<string> Helper(string s, int i, int j){
	List<string> output = new List<string>();

	for(int d = 1; d <= j-i; d++){
		string left = s.Substring(i, d);
		Console.WriteLine(i.ToString() + "-" + j.ToString() + "-" + d.ToString());
		string right = s.Substring(i+d, j-i-d);
		
		if((!left.StartsWith("0") || left.Equals("0")) && (!right.EndsWith("0"))){
		    output.Add(left + (d < j-i ? "." : "") + right);
		}
	}

	return output;
}
```
