---
title: Maximum Points You Can Obtain from Cards
date: "2020-04-26"
type: problem-solving
description: Maximum Points You Can Obtain from Cards
tags: csharp
---

Note: This problem was taken from LeetCode - [Maximum Points You Can Obtain from Cards](https://leetcode.com/problems/maximum-points-you-can-obtain-from-cards/)

### Dynamic Programming (Time Limit Exceeded)

```csharp
public int MaxScore(int[] cardPoints, int k) {
	Dictionary<int,int> memo = new Dictionary<int,int>();
	return this.MaxScore(cardPoints, 0, cardPoints.Length - 1, k, memo);
}

public int MaxScore(int[] cardPoints, int start, int end, int k, Dictionary<int,int> memo){
	if(k == 0 || start > end){
		return 0;
	}
	
	int memoLoc = (cardPoints.Length * start) + end;
	if(memo.ContainsKey(memoLoc)){
		return memo[memoLoc];
	}
	
	memo[memoLoc] = Math.Max(
		cardPoints[start] + this.MaxScore(cardPoints, start+1, end, k-1, memo),
		cardPoints[end] + this.MaxScore(cardPoints, start, end-1, k-1, memo)
	);
	
	return memo[memoLoc];
}
```

### Two Pointer Approach

```csharp
public int MaxScore(int[] cardPoints, int k) {
	int startPointer = -1;
	int endPointer = cardPoints.Length - k - 1;
	
	int sum = 0;
	
	for(int i = cardPoints.Length - k; i < cardPoints.Length; i++){
		sum += cardPoints[i];
	}
	
	int maxSum = sum;
	
	if(cardPoints.Length == k){
		return maxSum;
	}
	
	for(int i = 0; i < k; i++){
		startPointer++;
		endPointer++;
		
		sum = sum + cardPoints[startPointer] - cardPoints[endPointer];            
		maxSum = Math.Max(maxSum, sum);
	}
	return maxSum;
}
```
