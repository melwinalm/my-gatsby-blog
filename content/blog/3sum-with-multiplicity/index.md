---
title: 3Sum With Multiplicity
date: "2021-03-23"
type: problem-solving
description: 3Sum With Multiplicity
tags: csharp
---

Note: This problem was taken from LeetCode - [3Sum With Multiplicity](https://leetcode.com/problems/3sum-with-multiplicity/)

### Naive Approach

```csharp
public int ThreeSumMulti(int[] arr, int target) {
	int N = arr.Length;
	
	int count = 0;
	
	for(int i = 0; i < N; i++){
		for(int j = i+1; j < N; j++){
			for(int k = j+1; k < N; k++){
				if(arr[i] + arr[j] + arr[k] == target){
					count++;
				}
			}
		}
	}
	
	return count;
}
```

### Three Pointer Approach

```csharp
public int ThreeSumMulti(int[] arr, int target) {
	int N = arr.Length;
	
	Array.Sort(arr);
	
	int count = 0;
	
	for(int i = 0; i < N; i++){
		int T = target - arr[i];
		int j = i+1;
		int k = N-1;
		
		while(j < k){
			if(arr[j] + arr[k] < T){
				j++;
			}
			else if(arr[j] + arr[k] > T){
				k--;
			}
			else if(arr[j] != arr[k]){
				int left = 1;
				int right = 1;
				
				while(j+1 < k && arr[j] == arr[j+1]){
					left++;
					j++;
				}
				
				while(j < k-1 && arr[k-1] == arr[k]){
					right++;
					k--;
				}
				
				count += left * right;
				count %= 1000000007;
				
				j++;
				k--;
			}
			else{
				count += (k-j+1) * (k-j)/2;
				count %= 1000000007;
				break;
			}
		}
	}
	
	return count;
}
```
