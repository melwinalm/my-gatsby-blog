---
title: Maximum Number of Vowels in a Substring of Given Length
date: "2020-05-24"
type: problem-solving
description: Maximum Number of Vowels in a Substring of Given Length
tags: csharp
---

Note: This problem was taken from LeetCode - [Maximum Number of Vowels in a Substring of Given Length](https://leetcode.com/problems/maximum-number-of-vowels-in-a-substring-of-given-length/)

### Using Sliding Window

```csharp
public int MaxVowels(string s, int k) {
	if(k > s.Length){
		return 0;
	}
	
	int maxCount = 0;
	int currCount = 0;
	
	for(int i = 0; i < k; i++){
		currCount += this.IsVowel(s, i); 
	}
	
	maxCount = currCount;

	int index = k;
	
	while(index < s.Length){
		currCount += this.IsVowel(s, index) - this.IsVowel(s, index - k);
		maxCount = Math.Max(maxCount, currCount);
		index++;
	}
	
	return maxCount;
}

public int IsVowel(string s, int i){
	if(s[i] == 'a' || s[i] == 'e' || s[i] == 'i' || s[i] == 'o' || s[i] == 'u'){
		return 1;
	}
	
	return 0;
}
```
