---
title: Jewels and Stones
date: "2020-03-26"
type: problem-solving
description: Jewels and Stones
tags: csharp
---

Note: This problem was taken from LeetCode - [Jewels and Stones](https://leetcode.com/problems/jewels-and-stones/)

### Using HashSet

First, push all the jewels into a HashSet. Then loop through the stones and check if the stone exists in the `HashSet`. Increment the count on finding a Jewel. This count is the required result.

```csharp
public int NumJewelsInStones(string J, string S) {
    HashSet<char> Jewels = new HashSet<char>();
    
    for(int i = 0; i < J.Length; i++){
        Jewels.Add(J[i]);
    }
    
    int count = 0;
    
    for(int i = 0; i < S.Length; i++){
        if(Jewels.Contains(S[i])){
            count++;
        }
    }
    
    return count;
}
```
