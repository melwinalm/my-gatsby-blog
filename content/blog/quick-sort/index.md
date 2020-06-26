---
title: Sorting Algorithm - Quick Sort
date: "2020-06-26"
type: problem-solving
description: Sorting Algorithm - Quick Sort
tags: csharp
---

### Problem Statement

Sort integer array using Quick Sort

### Solution

In this sorting technique, you divide the given array into sub arrays and sort those sub arrays by selecting a pivot element.

```csharp
// Call this function to sort the array  - Sorting.QuickSort(arr, 0, arr.Length - 1);

public static class Sorting
{
	public static void QuickSort(int[] arr, int start, int end){
		if(start < end){
			int pIndex = Sorting.Partition(arr, start, end);
			
			Sorting.QuickSort(arr, start, pIndex-1);
			Sorting.QuickSort(arr, pIndex+1, end);
		}
	}
	
	public static int Partition(int[] arr, int start, int end){
		int pivot = arr[end]; // Last element of the sub array is considered as pivot
		
		int i = start - 1;
		
		for(int j = start; j <= end-1; j++){
			if(arr[j] < pivot){
				i++;
				Sorting.Swap(arr, i, j);
			}
		}
		
		Sorting.Swap(arr, i+1, end);
		return i + 1;
	}
	
	public static void Swap(int[] arr, int i, int j){
		int temp = arr[i];
		arr[i] = arr[j];
		arr[j] = temp;
	}
}
```

The above sorting technique has nlogn average time complexity. This sorting method used Divide and Conquer approach. This sorting approach sorts array using in-place method compared to merge sort which creates a temporary array to save the sorted elements of a sub array.
