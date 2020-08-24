---
title: Stream of Characters
date: "2020-08-24"
type: problem-solving
description: Stream of Characters
tags: csharp
---

Note: This problem was taken from LeetCode - [Stream of Characters](https://leetcode.com/problems/stream-of-characters/)

### Using Trie Data Structure

```csharp
public class StreamChecker {

    Trie root;
    StringBuilder sb;
    
    public StreamChecker(string[] words) {
        root = new Trie();
        sb = new StringBuilder();
        
        foreach(string word in words){
            int n = word.Length;
            Trie node = root;
            
            for(int i = n-1; i >= 0; i--){
                char c = word[i];
                
                if(node.next[c-'a'] == null){
                    node.next[c-'a'] = new Trie();
                }
                
                node = node.next[c-'a'];
            }
            node.isWord = true;
        }
    }
    
    public bool Query(char letter) {
        sb.Append(letter);
        Trie node = root;
        
        for(int i = sb.Length-1; i >= 0 && node != null; i--){
            char c = sb[i];
            
            node = node.next[c-'a'];
            if(node != null && node.isWord){
                return true;
            }
        }
        
        return false;
    }
}

public class Trie{
    public Trie[] next;
    public bool isWord;
    
    public Trie(){
        next = new Trie[26];
        isWord = false;
    }
}
```
