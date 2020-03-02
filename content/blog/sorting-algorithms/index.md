---
title: Search Algorithms
date: "2020-03-02"
type: algorithms
description: Search Algorithms
tags: csharp
---

### Linear Search

This search algorithm searches for the element by looking for the element in the whole array one at a time.

```csharp
int[] inpArray = new int[] {10, 5, 12, 34, 88, 23, 9};
int element = 23;

public int LinearSearch(int[] inpArray, int element){
    for(int i = 0; i < inpArray.Length; i++){
        if(inpArray[i] == element){
          // Return the index of the first occurence of the element in the array
          return i;
        }
    }

    // Return -1 if the element is not foud
    return - 1;
}
```

### Binary search

This search technique requires that the input array is sorted. Here, simply divide the given array in half and check if the element lies in the first or second half. Keep repeating this process to get the required result.

```csharp
int[] inpArray = new int[] {5, 9, 10, 12, 23, 34, 88};
int element = 23;

public int BinarySearch(int[] inpArray, int element)
{
    int low = 0;
    int high = inpArray.Length - 1;

    while (low <= high)
    {
        int mid = (low + high) / 2;
        if (inpArray[mid] == element)
        {
            return mid;
        }
        else if (inpArray[mid] < element)
        {
            low = mid + 1;
        }
        else
        {
            high = mid - 1;
        }
    }
    return -1;
}
```

| Algorithm | Input type | Time Complexity | Space Complexity |
| ------------- |:-------------:|:-------------:|:-----:|
| Linear Search | Data need not be sorted | O(n) | O(1) |
| Binary Search | Sorted Data required | O(log(n)) | O(1) |
