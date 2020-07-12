---
title: Number of Substrings With Only 1s
date: "2020-07-12"
type: problem-solving
description: Number of Substrings With Only 1s
tags: csharp
---

Note: This problem was taken from LeetCode - [Number of Substrings With Only 1s](https://leetcode.com/problems/number-of-substrings-with-only-1s/)

```csharp
public int NumSub(string s) {
	int totalCount = 0;
	int tempCount = 0;
	
	for(int i = 0 ; i < s.Length; i++){
		if(s[i] == '1'){
			tempCount++;
		}
		else{
			totalCount += this.SubCount(tempCount);
			tempCount = 0;
		}
		
	}
	
	totalCount += this.SubCount(tempCount);
	
	return totalCount;
}

public int SubCount(int n){
	long temp = 0;
	for(int i = 0; i <= n; i++){
		temp += n;
		temp %= 1000000007;
	}

	return (int)temp/2;
}
```
