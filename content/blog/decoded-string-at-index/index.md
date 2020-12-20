---
title: Decoded String at Index
date: "2020-12-20"
type: problem-solving
description: Decoded String at Index
---

Note: This problem was taken from LeetCode - [Decoded String at Index](https://leetcode.com/problems/decoded-string-at-index/)

### Naive Solution

```csharp
public string DecodeAtIndex(string S, int K) {
	StringBuilder text = new StringBuilder();
	
	int i = 0;
	
	while(i < S.Length){
		if(char.IsDigit(S[i])){
			int count = Convert.ToInt32(S[i] - 49);
			
			string temp = text.ToString();
			while(count > 0){
				text.Append(temp);
				count--;
			}
		}
		else{
			text.Append(S[i]);
		}
		
		if(text.Length >= K){
			return text[K-1].ToString(); 
		}
		
		i++;
	}
	
	return text[K-1].ToString();
}
```

### Better Solution

```csharp
public string DecodeAtIndex(string S, int K) {
	long size = 0;
	int N = S.Length;
	
	for(int i = 0; i < N; i++){
		if(Char.IsDigit(S[i])){
			size *= (S[i] - '0');
		}
		else{
			size++;
		}
	}
	
	for(int i = N-1; i >= 0; i--){
		K = (int)(K % size);
		
		if(K == 0 && !Char.IsDigit(S[i])){
			return S[i].ToString();
		}

		if(Char.IsDigit(S[i])){
			size /= S[i] - '0';
		}
		else{
			size--;
		}
	}
	
	return "";
}
```
