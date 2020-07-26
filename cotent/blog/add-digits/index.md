---
title: Add Digits
date: "2020-07-26"
type: problem-solving
description: Add Digits
tags: csharp
---

Note: This problem was taken from LeetCode - [Add Digits](https://leetcode.com/problems/add-digits/)

### Naive Approach

```csharp
public int AddDigits(int num) {
	int output = num;
	
	while(output > 9){
		output = this.FindSum(output);
	}
	
	return output;
}

public int FindSum(int num){
	int output = 0;
	
	while(num != 0){
		output += num % 10;
		num /= 10;
	}
	
	return output;
}
```

### Using Congruence Formula

```csharp
public int AddDigits(int num) {
	return 1 + (num - 1) % 9;
}
```
