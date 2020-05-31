---
title: Edit Distance
date: "2020-05-31"
type: problem-solving
description: Edit Distance
tags: csharp
---

Note: This problem was taken from LeetCode - [Edit Distance](https://leetcode.com/problems/edit-distance/)

### Using Top Down Approach (Time Limit Exceeded error)

```csharp
public int MinDistance(string word1, string word2) {
	return this.EditDistance(word1, word2, 0, 0);
}

public int EditDistance(string word1, string word2, int index1, int index2){
	if(index1 >= word1.Length && index2 >= word2.Length){
		return 0;
	}
	
	if(index1 == word1.Length){
		return word2.Length - index2;
	}
	
	if(index2 == word2.Length){
		return word1.Length - index1;
	}
	
	if(word1[index1] == word2[index2]){
		return this.EditDistance(word1, word2, index1 + 1, index2 + 1);
	}
	
	int insert = 1 + this.EditDistance(word1, word2, index1, index2 + 1);
	int delete = 1 + this.EditDistance(word1, word2, index1 + 1, index2);
	int replace = 1 + this.EditDistance(word1, word2, index1 + 1, index2 + 1);
	
	return Math.Min(insert, Math.Min(delete, replace));        
}
```

#### The time complexity of the above solution can be improved using Memoization

### Using Bottom Up Approach

```csharp
public int MinDistance(string word1, string word2) {
	int m = word1.Length;
	int n = word2.Length;
	
	int[,] dp = new int[m+1, n+1];
	
	// If one of the word is of length 0, then the edit distance will be the length of the word.
	for(int i = 0; i <= m; i++){
		dp[i,0]= i;
	}
	
	for(int i = 0; i <= n; i++){
		dp[0,i]= i;
	}
	
	for(int i = 1; i <= m; i++){
		for(int j = 1; j <= n; j++){
			if(word1[i-1] == word2[j-1]){
				dp[i,j] = dp[i-1,j-1];
			}
			else{
				dp[i,j] = 1 + Math.Min(dp[i-1,j], Math.Min(dp[i, j-1], dp[i-1,j-1]));
			}
		}
	}
	
	return dp[m,n];
}
```
