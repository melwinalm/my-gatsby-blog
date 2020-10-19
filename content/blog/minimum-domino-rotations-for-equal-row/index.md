---
title: Minimum Domino Rotations For Equal Row
date: "2020-10-19"
type: problem-solving
description: Minimum Domino Rotations For Equal Row
tags: csharp
---

Note: This problem was taken from LeetCode - [Minimum Domino Rotations For Equal Row](https://leetcode.com/problems/minimum-domino-rotations-for-equal-row/)

### Linear Time, Constant Space

```csharp
public int MinDominoRotations(int[] A, int[] B) {
	int[] ACount = new int[6];
	int[] BCount = new int[6];
	
	int N = A.Length;
	
	for(int i = 0; i < A.Length; i++){
		ACount[A[i]-1]++;
		BCount[B[i]-1]++;
	}
	
	int posNum = -1;
	
	for(int i = 0; i < 6; i++){
		if(ACount[i] + BCount[i] >= N){
			posNum = i+1;
			continue;
		}
	}
	
	if(posNum == -1){
		return -1;
	}
	
	int repNums = 0; // Number of times A and B have same values(posNum) at a index
	int count = 0;
	
	for(int i = 0; i < A.Length; i++){
		if(A[i] == posNum && B[i] == posNum){
			repNums++;
		}
		else if(A[i] == posNum || B[i] == posNum){
			if(A[i] == posNum){
				count++;                
			}
		}
		else{
			return -1;
		}
	}
	
	return Math.Min(count, N - count - repNums);
}
```

### Linear Time, Constant Space - Improved

```csharp
public int MinDominoRotations(int[] A, int[] B) {
	int[] ACount = new int[6];
	int[] BCount = new int[6];
	int[] SameCount = new int[6];
	
	int N = A.Length;
	
	for(int i = 0; i < A.Length; i++){
		ACount[A[i]-1]++;
		BCount[B[i]-1]++;
		
		if(A[i] == B[i]){
			SameCount[A[i]-1]++;
		}
		
	}
	
	int posNum = -1;
	
	for(int i = 0; i < 6; i++){
		if(ACount[i] + BCount[i] - SameCount[i] == N){
			return N - Math.Max(ACount[i], BCount[i]);
		}
	}
	
	return -1;        
}
```
