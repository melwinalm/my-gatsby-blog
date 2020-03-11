---
title: Assign Cookies
date: "2020-03-11"
type: problem-solving
description: Assign Cookies
tags: csharp
---

Note: This problem was taken from LeetCode - [Assign Cookies](https://leetcode.com/problems/assign-cookies/)

The highest number of children can be provided with the cookies by providing the biggest cookies to the children with the highest greed factor. So first sort both the greed factors and the cookie sizes. Then create two pointers each pointing to greed factor array and cookie size arrays. Starting both the pointers from the ends of the array, check if the cookie size is greater than or equal to the greed factor of a chile. If yes, then increase the counter and shift both the pointers by one step left. If not, then just decrement the greed pointer by one step. Keep doing this to get the required result. 

```csharp
public int FindContentChildren(int[] g, int[] s) {
    Array.Sort(g);
    Array.Sort(s);
    
    int gPointer = g.Length - 1;
    int sPointer = s.Length - 1;
    
    int count = 0;
    
    while(gPointer >= 0 && sPointer >= 0){
        if(s[sPointer] >= g[gPointer]){
            count++;
            gPointer--;
            sPointer--;
        }
        else{
            gPointer--;
        }
    }
    
    return count;
}
```
