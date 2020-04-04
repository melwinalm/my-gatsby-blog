---
title: How Many Numbers Are Smaller Than the Current Number
date: "2020-04-04"
type: problem-solving
description: How Many Numbers Are Smaller Than the Current Number
tags: csharp
---

Note: This problem was taken from LeetCode - [How Many Numbers Are Smaller Than the Current Number](https://leetcode.com/problems/how-many-numbers-are-smaller-than-the-current-number/)

### Brute Force Approach

Check every element in the input array with the remaining elements and increase the counter on finding a smaller number.

```csharp
public int[] SmallerNumbersThanCurrent(int[] nums) {
    int n = nums.Length;
    
    int[] output = new int[n];
    
    for(int i = 0; i < n; i++){
        for(int j = 0; j < n; j++){
            if(nums[i] > nums[j]){
                output[i]++;
            }
        }
    }
    
    return output;
}
```

### Sorting Approach

Initially sort the given array. Once sorted, iterate through the array and find the numbers smaller than the current number and put those values in a dictionary. Now construct the output using the dictionary values.

```csharp
public int[] SmallerNumbersThanCurrent(int[] nums) {
    int n = nums.Length;
    
    int[] output = new int[n];
    
    // The array needs to be cloned since the output has to be returned in the input array format
    int[] numsClone = (int[])nums.Clone();
    
    Array.Sort(numsClone);
    
    Dictionary<int,int> tempDict = new Dictionary<int,int>();
    tempDict[numsClone[0]] = 0;
    
    for(int i = 1; i < n; i++){
        // If the numbers are same then they need not be aaded to the dictionary
        if(numsClone[i] != numsClone[i-1]){ 
            // Index will give you the count of numbers smaller than the current number
            tempDict[numsClone[i]] = i;
        }
    }
    
    for(int i = 0; i < n; i++){
        output[i] = tempDict[nums[i]];
    }
    
    return output;
}
```

| Approach | Time Complexity | Space Complexity |
| ------------- |:-------------:| :-----:|
| Brute Force | O(n^2) | O(n) |
| Sorting & Dictionary | O(nlogn) | O(n) |
