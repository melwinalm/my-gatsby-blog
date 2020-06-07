---
title: The k Strongest Values in an Array
date: "2020-06-07"
type: problem-solving
description: The k Strongest Values in an Array
tags: csharp
---

Note: This problem was taken from LeetCode - [The k Strongest Values in an Array](https://leetcode.com/problems/the-k-strongest-values-in-an-array/)

### Using Custom Comparator for Sorting

```csharp
public class Solution {
    public int[] GetStrongest(int[] arr, int k) {
		// Step 1: Sort the array and find the median as per definition given in the problem
        Array.Sort(arr);
        int N = arr.Length;
        int med = arr[(N - 1)/2];
        
		// Step 2: Find the absolute difference between the array value and median and store them in a new array.
        int[][] medArray = new int[N][];
        
        for(int i = 0; i < N; i++){
            medArray[i] = new int[2];
            medArray[i][0] = arr[i];
            medArray[i][1] = Math.Abs(med - arr[i]);
        }
        
		// Step 3: Sort the array as per the conditions in the problem statement using custom comapator function
        Array.Sort(medArray, new CustomComparator());

		// Step 4: Output the first k elements of the sorted array
        int[] output = new int[k];
        for(int i = 0; i < k; i++){
            output[i] = medArray[i][0];
        }
        
        return output;
    }
}

public class CustomComparator: IComparer<int[]>{
    public int Compare(int[] value1, int[] value2){
        if(value1[1] == value2[1]){
            return value2[0] - value1[0];
        }
        else {
            return value2[1] - value1[1];
        }
    }
}
