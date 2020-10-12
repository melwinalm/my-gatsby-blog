---
title: Buddy Strings
date: "2020-10-12"
type: problem-solving
description: Buddy Strings
tags: csharp
---

Note: This problem was taken from LeetCode - [Buddy Strings](https://leetcode.com/problems/buddy-strings/)

### Naive Solution

```csharp
public bool BuddyStrings(string A, string B) {
	if(A.Length != B.Length){
		return false;
	}
	
	if(A == B){
		int[] count = new int[26];
		
		for(int i = 0; i < A.Length; i++){
			count[A[i] - 'a']++;
			
			if(count[A[i] - 'a'] > 1){
				return true;
			}
		}

		return false;
	}
	else{
		
		int first = -1;
		int second = -1;
		
		for(int i = 0; i < A.Length; i++){
			if(A[i] != B[i]){
				if(first == -1){
					first = i;
				}        
				else if(second == -1){
					second = i;
				}
				else{
					return false;
				}
			}
		}
		
		return second != -1 && A[first] == B[second] && A[second] == B[first];
	}
}
```
