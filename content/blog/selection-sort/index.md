---
title: Sorting Algorithm - Selection Sort
date: "2020-06-23"
type: problem-solving
description: Sorting Algorithm - Selection Sort
tags: csharp
---

### Problem Statement

Sort integer array using Selection Sort

### Solution

In this sorting technique, during each iteration, find the smallest element by scanning through each element and then swap it with the element at the current index.

```csharp
public void SelectionSort(int[] arr){
	int N = arr.Length;
	
	for(int i = 0; i < N; i++){
		int minIndex = i;
		
		for(int j = i+1; j < N; j++){
			if(arr[j] < arr[minIndex]){
				minIndex = j;	
			}
		}
		
		int temp = arr[minIndex];
		arr[minIndex] = arr[i];
		arr[i] = temp;
	}
}
```

The above sorting technique has quadratic time complexity and constant space requirement. This sorting technique takes only O(n) swaps, so this approach should be preferred when the write operation is costly.
