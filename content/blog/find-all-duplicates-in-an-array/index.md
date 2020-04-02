---
title: Find All Duplicates in an Array
date: "2020-04-02"
type: problem-solving
description: Find All Duplicates in an Array
tags: csharp
---

Note: This problem was taken from LeetCode - [Find All Duplicates in an Array](https://leetcode.com/problems/find-all-duplicates-in-an-array/)

### Approach 1

In this approach, first, we try to move all the numbers to their respective indices except for the repeated indices. Consider the following example:

```
[4,3,2,7,8,2,3,1]
```
Moving the numbers to respective indices will turn the array into:
```
[1,2,3,4,2,3,7,8]
```

Once this is constructed now iterate through this array and check if the index and their value match(here considering the index of an array starts from 1). If they don't match then put those values in a separate array and return it.

```csharp
public IList<int> FindDuplicates(int[] nums) {
    List<int> output = new List<int>();
    int n = nums.Length;
    
    int i = 0;
    
    while(i < n){
        if(nums[nums[i] - 1] != nums[i] && nums[i] - 1 != i){
            this.Swap(nums, nums[i] - 1, i);
        }
        else{
            i++;
        }
    }
    
    for(int j = 0; j < n; j++){
        if(nums[j] - 1 != j){
            output.Add(nums[j]);
        }
    }
    
    return output;
}

public void Swap(int[] arr, int i, int j){
    int temp = arr[i];
    arr[i] = arr[j];
    arr[j] = temp;
}
```

### Approach 2

Iterate through the given array and negate the value at the index where the current value is pointing. If you find a value which is already negated, it means that the number is repeated. Put that number in a separate list. Repeat this throughout the array to get the repeated numbers in the given array.

```csharp
public IList<int> FindDuplicates(int[] nums) {
    List<int> output = new List<int>();
    int n = nums.Length;
    
    for(int i = 0 ; i < n; i++){
        int index = Math.Abs(nums[i]);
        
        if(nums[index - 1] > 0){
            nums[index - 1] = -nums[index - 1];
        }
        else{
            output.Add(index);
        }
    }        
    
    return output;
}
```

#### Note: The given question says that the input values are in the range 1 <= a[i] <= n. And the index of these values will be in the range 0 <= i < n. We use the properties of array indices to find the solution in the above two approaches.
