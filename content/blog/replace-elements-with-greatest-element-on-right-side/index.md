---
title: Replace Elements with Greatest Element on Right Side
date: "2020-03-27"
type: problem-solving
description: Replace Elements with Greatest Element on Right Side
tags: csharp
---

Note: This problem was taken from LeetCode - [Replace Elements with Greatest Element on Right Side](https://leetcode.com/problems/replace-elements-with-greatest-element-on-right-side/)

### Scan from Right to Left

Scan from the rightmost element of the array towards left. Store the maximum number in a variable as you scan through the array. As you scan if a new `maxNum` is found then replace it. Keep doing this until the 0th index of the array.

```csharp
public int[] ReplaceElements(int[] arr) {
    int[] output = new int[arr.Length];
    
    output[arr.Length - 1] = -1;
    int maxNum = arr[arr.Length - 1];
    
    for(int i = arr.Length - 2; i >= 0; i--){
        output[i] = maxNum;
        if(arr[i] > maxNum){
            maxNum = arr[i];
        }
    }
    
    return output;
}
```
