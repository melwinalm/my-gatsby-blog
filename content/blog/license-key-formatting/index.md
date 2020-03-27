---
title: License Key Formatting
date: "2020-03-27"
type: problem-solving
description: License Key Formatting
tags: csharp
---

Note: This problem was taken from LeetCode - [License Key Formatting](https://leetcode.com/problems/license-key-formatting/)

```csharp
public string LicenseKeyFormatting(string S, int K) {
    StringBuilder output = new StringBuilder();
    
    int i = S.Length - 1;
    int count = 0;
    
    while(i >= 0){
        char c = char.ToUpper(S[i]);
        if(c == '-'){
            i--;
        }
        else if(count != 0 && count % K == 0){
            output.Insert(0, '-');
            count = 0;
        }
        else{
            output.Insert(0, c);
            count++;
            i--;
        }
    }
    
    return output.ToString();
}
```
