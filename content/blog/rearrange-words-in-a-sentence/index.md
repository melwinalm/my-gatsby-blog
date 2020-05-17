---
title: Rearrange Words in a Sentence
date: "2020-05-17"
type: problem-solving
description: Rearrange Words in a Sentence
tags: csharp
---

Note: This problem was taken from LeetCode - [Rearrange Words in a Sentence](https://leetcode.com/problems/rearrange-words-in-a-sentence/)

### Naive Method

```csharp
    public string ArrangeWords(string text) {
        if(text.Length == 0){
            return "";
        }

        Dictionary<int, List<string>> map = new Dictionary<int, List<string>>();
        List<int> temp = new List<int>();

        string[] words = text.ToLower().Split(' ');

        foreach(string word in words){
            int len = word.Length;
            if(!map.ContainsKey(len)){
                map[len] = new List<string>();
                temp.Add(len);
            }
            map[len].Add(word);
        }

        int[] lengths = temp.ToArray();
        Array.Sort(lengths);

        StringBuilder output = new StringBuilder();

        foreach(int length in lengths){
            for(int i = 0; i < map[length].Count; i++){
                output.Append(map[length][i] + " ");
            }
        }

        output.Remove(output.Length - 1, 1);

        char c = Char.ToUpper(output[0]);
        output.Remove(0,1);
        output.Insert(0, c);

        return output.ToString();
    }
```
