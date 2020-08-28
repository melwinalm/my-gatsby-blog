---
title: Implement Rand10() Using Rand7()
date: "2020-08-28"
type: problem-solving
description: Implement Rand10() Using Rand7()
tags: csharp
---

Note: This problem was taken from LeetCode - [Implement Rand10() Using Rand7()](https://leetcode.com/problems/implement-rand10-using-rand7/)

### Using Rejection Sampling Technique

```csharp
public int Rand10() {
	int row;
	int col;
	int val;
	
	do {
		row = this.Rand7();
		col = this.Rand7();
		
		// -1 is subtracted to convert it to 0th index
		val = (col-1) + (row-1) * 7;
	} while(val > 40);
	
	// +1 is added to to convert it back to 1th index
	return (val % 10) + 1;
}
```
