---
title: Number of Ways Where Square of Number Is Equal to Product of Two Numbers
date: "2020-09-06"
type: problem-solving
description: Number of Ways Where Square of Number Is Equal to Product of Two Numbers
tags: csharp
---

Note: This problem was taken from LeetCode - [Number of Ways Where Square of Number Is Equal to Product of Two Numbers](https://leetcode.com/problems/number-of-ways-where-square-of-number-is-equal-to-product-of-two-numbers/)

### Using Dictionary

```csharp
public int NumTriplets(int[] nums1, int[] nums2) {
	Dictionary<long, int> num1Squares = new Dictionary<long,int>();
	Dictionary<long, int> num2Squares = new Dictionary<long,int>();
	
	foreach(int num in nums1){
		long square = (long)num * (long)num;
		if(!num1Squares.ContainsKey(square)){
			num1Squares[square] = 0;
		}
		
		num1Squares[square] += 1;
	}
	
	foreach(int num in nums2){
		long square = (long)num * (long)num;
		if(!num2Squares.ContainsKey(square)){
			num2Squares[square] = 0;
		}
		
		num2Squares[square] += 1;
	}
	
	int count = 0;
	
	for(int i = 0; i < nums1.Length; i++){
		for(int j = i+1; j < nums1.Length; j++){
			long prod = (long)nums1[i] * (long)nums1[j];
			if(num2Squares.ContainsKey(prod)){
				count += num2Squares[prod];
			}
		}
	}
	
	for(int i = 0; i < nums2.Length; i++){
		for(int j = i+1; j < nums2.Length; j++){
			long prod = (long)nums2[i] * (long)nums2[j];
			if(num1Squares.ContainsKey(prod)){
				count += num1Squares[prod];
			}
		}
	}
	
	return count;
}
```
