---
title: Count Sorted Vowel Strings
date: "2020-11-01"
type: problem-solving
description: Count Sorted Vowel Strings
tags: csharp
---

Note: This problem was taken from LeetCode - [Count Sorted Vowel Strings](https://leetcode.com/problems/count-sorted-vowel-strings/)

### Using Top Down Approach

```csharp
public int CountVowelStrings(int n) {
	int[] vowels = new int[] {1,2,3,4,5};
	
	int count = 0;
		
	for(int i = 0; i < 5; i++){
		count += this.DP(vowels, i, n-1);
	}
	
	return count;
	
}

public int DP(int[] vowels, int currIndex, int remNum){
	if(remNum == 0){
		return 1;
	}
	
	if(currIndex >= vowels.Length){
		return 0;
	}
	
	int count = 0;
	
	for(int a = currIndex; a < vowels.Length; a++){
		count += this.DP(vowels, a, remNum-1);
	}
	
	return count;
}
```

### Using Bottom Up Approach

TBW

### Using Bottom Up Approach (Space Improved)

TBW
