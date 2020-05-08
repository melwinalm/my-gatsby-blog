---
title: Count of substrings with only 1s
date: "2020-05-08"
type: problem-solving
description: Count of substrings with only 1s
tags: csharp
---

### Problem Statement

Given a binary string (consisting of 0s and 1s), return the count of substrings with only 1s.

### Using patterns

1 => one 1's => 1 = 1
2 => two 1's, one 2's => 2 + 1 = 3
3 => three 1's, two 2's, one 3's => 3 + 2 + 1 = 6
4 => four 1's, three 2's, two 3's, one 4's => 4 + 3 + 2 + 1 = 10

Looking at the above patterns we can generalize that for n subsequent ones, the substring count will be n(n+1)/2.

Apply this method throughout the given string array to get the desired result.

```csharp
public int SubstringCount(string s)
{
	int count = 0;

	int tempCount = 0;
	foreach(char c in s)
	{
		if(c == '1')
		{
			tempCount++;
		}
		else
		{
			count += this.Count(tempCount);
			tempCount = 0;
		}
	}

	count += this.Count(tempCount);

	return count;
}

public int Count(int n)
{
	if(n == 0)
	{
		return 0;
	}
	return (n * (n + 1))/ 2;
}
```

### TestCases

- 1           // 1
- 11          // 3
- 111         // 6
- 01110       // 6
- 0011100110  // 9
- 001111110   // 21
