---
title: Sorting Algorithm - Bubble Sort
date: "2020-05-11"
type: problem-solving
description: Selection Algorithm - Bubble Sort
tags: csharp
---

### Problem Statement

Sort integer array using Bubble Sort

### Solution

```csharp
public void BubbleSort(int[] arr)
{
	for(int i = 0; i < arr.Length; i++)
	{
		for(int j = i+1; j < arr.Length; j++)
		{
			if(arr[i] > arr[j])
			{
				int temp = arr[i];
				arr[i] = arr[j];
				arr[j] = temp;
			}
		}
	}
}
```

The above sorting technique has quadratic time complexity
