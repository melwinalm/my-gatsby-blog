---
title: Longest Common Prefix
date: "2020-02-28"
type: problem-solving
description: Longest Common Prefix
tags: csharp
---

Note: This problem was taken from LeetCode - [Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/)

### Brute Force Approach

Initially find the string with the smallest length out of the given strings. Then loop through all the strings character by character and check if the characters match. Add the character to an output string whenever the character is found in all the strings. Repeat this until the `smallest string length` to get the desired result.

```csharp
public string LongestCommonPrefix(string[] strs) {
    
    if (strs.Length == 0){
        return "";
    }
    
    int sLength = strs[0].Length;
    string output = "";
    
    // Finding the string with the smallest length
    for(int i = 1 ; i < strs.Length ; i++){
        if(strs[i].Length < sLength){
            sLength = strs[i].Length;
        }
    }
    
    if (sLength == 0){
        return "";
    }
    
    for (int i = 0 ; i < sLength ; i++){
        for (int j = 0 ; j < strs.Length ;j++){
            if (strs[0][i] != strs[j][i]){
                return output;
            }
        }
        output += strs[0][i];
    }
    return output;
}
```

### Trie Approach

This problem can be solved using a Trie data structure as well.
