---
title: Search a 2D Matrix
date: "2020-02-21"
type: problem-solving
description: Search a 2D Matrix
tags: csharp
---

Note: This problem was taken from LeetCode - [Search a 2D Matrix](https://leetcode.com/problems/search-a-2d-matrix/)

### Naive Approach

The naive approach to solve this would be to go through every element in the array and check if the target number matches any one of them.

This solution has a time complexity of O(m*n) and space complexity of O(1).

### Binary Search

Perform a simple binary search operation on the given 2D matrix iteratively to check if any number matches the given target number.

```csharp
public bool SearchMatrix(int[][] matrix, int target) {
    int rows = matrix.Length;
    
    // Checks if the matrix is a 0 x 0 matrix
    if(rows == 0){
        return false;
    }
    
    int columns = matrix[0].Length;
    
    int start = 0;
    int end = (rows * columns) - 1;
    
    while(start <= end){
        int mid = (start + end) / 2;
        int midval = matrix[mid / columns][mid % columns];
        
        if(midval == target){
            return true;
        }
        else if (midval < target){
            start = mid + 1;
        }
        else{
            end = mid - 1;
        }
    }
    return false;
}
```

This solution has a time complexity of O(log(m*n)) and space complexity of O(1).

| Approach | Time Complexity | Space Complexity |
| ------------- |:-------------:| :-----:|
| Naive Approach | O(m*n) | O(1) |
| Binary Search | O(log(m*n)) | O(1) |
