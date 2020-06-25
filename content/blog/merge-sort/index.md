---
title: Sorting Algorithm - Merge Sort
date: "2020-06-25"
type: problem-solving
description: Sorting Algorithm - Merge Sort
tags: csharp
---

### Problem Statement

Sort integer array using Merge Sort

### Solution

In this sorting technique, you divide the given array into sub arrays and sort those sub arrays and merge them to get the sorted array

```csharp

// Call this function to sort the array
this.MergeSort(arr, 0, arr.Length-1);

public static void MergeSort(int[] arr, int start, int end){
	if(start < end){
		int mid = (start + end) / 2;
		
		Sorting.MergeSort(arr, start, mid);
		Sorting.MergeSort(arr, mid+1, end);
		Sorting.Merge(arr, start, mid, end);
	}
}

// Using two pointer approach
public static void Merge(int[] arr, int start, int mid, int end){
	int[] tempArr = new int[end - start + 1];
	
	int fIndex = start;
	int sIndex = mid + 1;
	
	int i = 0;
	
	// Traverse both array groups and add smaller elements to the temp array
	while(fIndex <= mid && sIndex <= end){
		if(arr[fIndex] <= arr[sIndex]){
			tempArr[i] = arr[fIndex];
			fIndex++;
		}
		else{
			tempArr[i] = arr[sIndex];
			sIndex++;
		}
		i++;
	}
	
	// Copy remaining elements
	while(fIndex <= mid){
		tempArr[i] = arr[fIndex];
		fIndex++;
		i++;
	}
	
	// Copy remaining elements
	while(sIndex <= end){
		tempArr[i] = arr[sIndex];
		sIndex++;
		i++;
	}
	
	// Copy elements from temp array to original array
	for(int a = start; a <= end; a++){
		arr[a] = tempArr[a-start];
	}
}
```

The above sorting technique has nlogn time complexity and linear space requirement. This sorting method used Divide and Conquer approach.
