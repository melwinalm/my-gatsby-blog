---
title: Largest Number
date: "2020-06-04"
type: problem-solving
description: Largest Number
tags: csharp
---

Note: This problem was taken from LeetCode - [Largest Number](https://leetcode.com/problems/largest-number/)

### Using Custom Comparator Class

```csharp
public class Solution {
    public string LargestNumber(int[] nums) {
        string[] arr = new string[nums.Length];
        
        // Converts the given array to string array
        for(int i = 0; i < nums.Length; i++){
            arr[i] = nums[i].ToString();
        }
        
        // Sort string in descending order
        Array.Sort(arr, new CustomComparator());
        
        string output = "";
        
        // If the output is [0,0...] then return output should be "0" and not "00"
        if(arr[0] == "0"){
            return "0";
        }
        
        // Concatenating the sorted array
        for(int i = 0; i < nums.Length; i++){
            output += arr[i];
        }
        
        return output;
    }
}

// Custom Comparator function
public class CustomComparator : IComparer<string>{
    public int Compare(string a, string b){
        string temp1  = a + b;
        string temp2 = b + a;
        
        return string.Compare(temp2, temp1);
    }
}
```
