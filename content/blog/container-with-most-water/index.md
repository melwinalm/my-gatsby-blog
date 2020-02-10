---
title: Container With Most Water
date: "2020-01-27"
type: problem-solving
description: Container With Most Water
tags: csharp
---

Note: This problem was taken from LeetCode - [Container With Most Water](https://leetcode.com/problems/container-with-most-water/)

### Brute Force Method

Brute force way to solve this problem would be to try every combination of input and check which one generates the maximum area. 

The time complexity of this approach is O(n^2) and space complexity is O(1). Check the next solution which solves this problem in linear time.

### Two pointer Method

In the Two Pointer approach, we use a start and an end pointer. Keep moving these pointers closer to the middle based on their heights. If one pointer is higher than the other then move the other pointer closer to the center. Keep repeating this to find get the desired result. 

```csharp
public int MaxArea(int[] height) {
    int max = 0;
    int start = 0;
    int end = height.Length - 1;
    
    while(start < end){
        int temp = Math.Min(height[start], height[end]) * (end - start);
        
        if(temp > max){
            max = temp;
        }
        
        if(height[start] > height[end]){
            end--;
        }
        else{
            start++;
        }
    }
    return max;
}
```

The above solution has a time complexity of O(n) and space complexity of O(1).
