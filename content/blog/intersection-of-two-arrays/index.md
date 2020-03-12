---
title: Intersection of Two Arrays
date: "2020-03-12"
type: problem-solving
description: Intersection of Two Arrays
tags: csharp
---

Note: This problem was taken from LeetCode - [Intersection of Two Arrays](https://leetcode.com/problems/intersection-of-two-arrays/)

### Naive Approach

Initially push the contents of both the arrays to two different `HashSets`. Now loop through all the contents of one `HashSet` and check if the second `HashSet` has that value. If yes, then add those values to a new list. This should give you the required result.

```csharp
public int[] Intersection(int[] nums1, int[] nums2) {
    HashSet<int> set1 = new HashSet<int>();
    HashSet<int> set2 = new HashSet<int>();
    
    for(int i = 0; i < nums1.Length; i++){
        set1.Add(nums1[i]);
    }
    
    for(int i = 0; i < nums2.Length; i++){
        set2.Add(nums2[i]);
    }
    
    List<int> output = new List<int>();
    
    foreach(int key in set1){
        if(set2.Contains(key)){
            output.Add(key);
        }
    }
    
    return output.ToArray();
}
```

This solution has a time complexity of O(m + n) and space complexity of O(m + n) where m and n are the sizes of both the arrays.
