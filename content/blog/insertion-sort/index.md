---
title: Sorting Algorithm - Insertion Sort
date: "2020-06-23"
type: problem-solving
description: Sorting Algorithm - Insertion Sort
tags: csharp
---

### Problem Statement

Sort integer array using Insertion Sort

### Solution

In this sorting technique, you take an element at ith index and check if that fits between 0 to i-1th index and place it where it fits. Repeat this from throughout the array to sort the array.

```csharp
public static void InsertionSort(int[] arr){
	int N = arr.Length;
	
	for(int i = 1; i < N; i++){
		int key = arr[i];
		int j = i - 1;
		
		while(j >= 0 && arr[j] > key){
			arr[j+1] = arr[j];
			j--;
		}
		arr[j+1] = key;
	}
}
```

The above sorting technique has quadratic time complexity and constant space requirement. This sorting is useful when the input array is almost sorted, only a few elements are misplaced.
