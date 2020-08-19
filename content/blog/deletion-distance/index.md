---
title: Deletion Distance
date: "2020-08-19"
type: problem-solving
description: Deletion Distance
tags: csharp
---

### Problem Statement

The deletion distance of two strings is the minimum number of characters you need to delete in the two strings in order to get the same string. For instance, the deletion distance between "heat" and "hit" is 3:

- By deleting 'e' and 'a' in "heat", and 'i' in "hit", we get the string "ht" in both cases.
- We cannot get the same string from both strings by deleting 2 letters or fewer.

Given the strings str1 and str2, write an efficient function deletionDistance that returns the deletion distance between them. Explain how your function works, and analyze its time and space complexities.

### Bottom Up Approach

Take the example of `dog` and `frog`. Three characters will have to be removed to match the strings.

```
	""	d	o	g
""	0	1	2	3
f	1	2	3	4
r	2	3	4	5
o	3	4	3	4
g	4	5	4	3
```

```csharp
public static int DeletionDistance(string str1, string str2)
{
  int m = str1.Length;
  int n = str2.Length;
  
  int[,] memo = new int[m+1, n+1];
  
  for(int i = 0; i <= m; i++){
	for(int j = 0; j <= n; j++){
	  if(i == 0){
		memo[i,j] = j;
	  }
	  else if(j == 0){
		memo[i,j] = i;
	  }
	  else if(str1[i-1] == str2[j-1]){
		memo[i,j] = memo[i-1,j-1];
	  }
	  else{
		memo[i,j] = 1 + Math.Min(memo[i-1,j], memo[i, j-1]);
	  }
	}
  }
  
  return memo[m,n];
}
```

### Bottom Up Approach (Space Optimized)

```csharp
public static int DeletionDistance(string str1, string str2)
{
  string minStr = str1.Length < str2.Length ? str1 : str2;
  string maxStr = str1.Length < str2.Length ? str2 : str1;
  
  int m = minStr.Length;
  int n = maxStr.Length;
  
  int[] prevMemo = new int[m+1];
  int[] currMemo = new int[m+1];
  
  for(int i = 0; i <= n; i++){
	for(int j = 0; j <= m; j++){
	  if(i == 0){
		currMemo[j] = j;
	  }
	  else if(j == 0){
		currMemo[j] = i;
	  }
	  else if(maxStr[i-1] == minStr[j-1]){
		currMemo[j] = prevMemo[j-1];
	  }
	  else{
		currMemo[j] = 1 + Math.Min(currMemo[j-1], prevMemo[j]);
	  }
	}
	
	prevMemo = currMemo;
	currMemo = new int[m+1];
	
  }
  
  return prevMemo[m];
}
```
