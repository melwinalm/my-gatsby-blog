---
title: Sort Array By Parity
date: "2020-03-05"
type: problem-solving
description: Sort Array By Parity
tags: csharp
---

Note: This problem was taken from LeetCode - [Sort Array By Parity](https://leetcode.com/problems/sort-array-by-parity/)

### Naive Approach

Th naive approach would be to loop through the array add even elements to a new array. Then loop again from start to end of the array and add odd elements of the array.

This has a time complexity of O(n) and space complexity of O(n).

### Two Pointer Approach (In-place)

Here we use two pointers to achieve the solution. Start pointer points to even numbers and end pointer points to odd numbers. Increment the start pointer and check for an odd number. When you find an odd number stop the loop. Do the same with the end pointer also. So, now the start pointer is pointing to an odd number and the end pointer is pointing to an even number. Swap the values in the start and end pointer. Repeat this until both the pointers meet to get the solution. 

```csharp
public int[] SortArrayByParity(int[] A) {
    if(A.Length < 2){
        return A;
    }
    
    int start = 0;
    int end = A.Length - 1;
    
    while(start <= end){
        while(start <= end && A[start] % 2 == 0){
            start++;
        }
        
        while(start <= end && A[end] % 2 != 0){
            end--;
        }
        
        if(start <= end){
            int temp = A[start];
            A[start] = A[end];
            A[end] = temp;

            start++;
            end--;
        }
    }
    
    return A;
}
```

This solution has a time complexity of O(n) and space complexity of O(1).

| Approach | Time Complexity | Space Complexity |
| ------------- |:-------------:| :-----:|
| Naive Approach | O(n) | O(n) |
| Two Pointer Approach | O(n) | O(1) |
