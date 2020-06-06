---
title: Queue Reconstruction by Height
date: "2020-06-06"
type: problem-solving
description: Queue Reconstruction by Height
tags: csharp
---

Note: This problem was taken from LeetCode - [Queue Reconstruction by Height](https://leetcode.com/problems/queue-reconstruction-by-height/)

### Using Custom Sort

First, sort the given array in the decreasing order of their heights. If two have same heights then sort them in the ascending order of k. After sorting, iterate through the array and insert them in the correct order based on their index value. This should give you the required result.

```csharp
public class Solution {
    public int[][] ReconstructQueue(int[][] people) {
        Array.Sort(people, new CustomComparator());
        
        List<int[]> output = new List<int[]>();
        
        foreach(int[] item in people){
            output.Insert(item[1], item);
        }
        
        return output.ToArray();
    }
}

public class CustomComparator: IComparer<int[]> {
    public int Compare(int[] index1, int[] index2){
        if(index1[0] == index2[0]){
            return index1[1] - index2[1];
        }
        else{
            return index2[0] - index1[0];
        }
    }
}
```
