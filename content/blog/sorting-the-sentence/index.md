---
title: FSorting the Sentence
date: "2021-05-16"
type: problem-solving
description: Sorting the Sentence
tags: csharp
---

Note: This problem was taken from LeetCode - [Sorting the Sentence](https://leetcode.com/problems/sorting-the-sentence/)

### Naive Approach

```csharp
public string SortSentence(string s) {
    string[] words = s.Split(' ');
    Array.Sort(words, (a,b) => a[a.Length-1] - b[b.Length-1]);
    
    string output = "";
    for(int i = 0; i < words.Length; i++){
        output += words[i].Substring(0, words[i].Length-1);
        if(i < words.Length-1){
            output += " ";
        }
    }
    
    return output;
}
```
