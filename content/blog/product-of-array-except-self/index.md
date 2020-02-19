---
title: Product of Array Except Self
date: "2020-02-11"
type: problem-solving
description: Product of Array Except Self
tags: csharp
---

Note: This problem was taken from LeetCode - [Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/)

### Left and Right Product Approach (With Additional Space)

Find the product of array elements starting from left to right and store it in `left` array. Repeat the same from right to left and save it in the `right` array. Now find the product every item from left and right, that will be the required result.

```csharp
public int[] ProductExceptSelf(int[] nums) {
    int N = nums.Length;
    
    int[] left = new int[N];
    int[] right = new int[N];
    int[] output = new int[N];
    
    left[0] = 1;
    
    for(int i = 1; i < N; i++){
        left[i] = nums[i-1] * left[i-1];
    }
    
    right[N-1] = 1;
    
    for(int i = N-2; i >= 0; i--){
        right[i] = nums[i+1] * right[i+1];
    }
    
    for(int i = 0; i < N; i++){
        output[i] = left[i] * right[i];
    }
    return output;
}
```

This solution has a time and space complexity of O(N).

### Left and Right Product Approach (Without Additional Space)

This solution is similar to the previous approach except that it doesn't require additional space two arrays.

```csharp
public int[] ProductExceptSelf(int[] nums) {
        int N = nums.Length;
        
        int[] output = new int[N];
        
        output[0] = 1;
        
        for(int i = 1; i < N; i++){
            output[i] = nums[i-1] * output[i-1];
        }
        
        int right = 1;
        
        for(int i = N-1; i >= 0; i--){
            output[i] = output[i] * right;
            right *= nums[i];
        }
        
        return output;
    }
```

Even this solution has line time and space complexity. The only difference between this and the previous approach is that this method doesn't use additional space to store two different arrays.
