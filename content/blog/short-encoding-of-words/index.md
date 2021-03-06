---
title: Short Encoding of Words
date: "2021-03-05"
type: problem-solving
description: Short Encoding of Words
tags: csharp
---

Note: This problem was taken from LeetCode - [Short Encoding of Words](https://leetcode.com/problems/short-encoding-of-words/)

### Using Trie

```csharp
public class Solution {
    public int MinimumLengthEncoding(string[] words) {
        TrieNode root = new TrieNode();
        
        Dictionary<TrieNode, int> map = new Dictionary<TrieNode, int>();
        
        for(int i = 0; i < words.Length; i++){
            string currWord = words[i];
            TrieNode temp = root;
            
            for(int j = currWord.Length-1; j >= 0; j--){
                temp = temp.Get(currWord[j]);
            }
            
            map[temp] = i;
        }
        
        int output = 0;
        
        foreach(var item in map){
            TrieNode tempNode = item.Key;
            
            if(tempNode.count == 0){
                output += words[map[tempNode]].Length + 1;
            }
        }
        
        return output;
    }
}

public class TrieNode{
    TrieNode[] children;
    public int count;

    public TrieNode(){
        children = new TrieNode[26];
        count = 0;
    }
    
    public TrieNode Get(char c){
        if(children[c - 'a'] == null){
            children[c - 'a'] = new TrieNode();
            count++;
        }
        
        return children[c - 'a'];
    }
}
```
