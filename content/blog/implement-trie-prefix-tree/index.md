---
title: Implement Trie (Prefix Tree)
date: "2020-05-14"
type: problem-solving
description: Implement Trie (Prefix Tree)
tags: csharp
---

Note: This problem was taken from LeetCode - [Implement Trie (Prefix Tree)](https://leetcode.com/problems/implement-trie-prefix-tree/)

### Trie Data Structure

```csharp
public class Trie {
    
    public class Node{
        public bool isEnd;
        public Node[] values;
        
        public Node(bool _isEnd){
            this.isEnd = _isEnd;
            this.values = new Node[26];
        }
    }

    /** Initialize your data structure here. */

    Node root;
    
    public Trie() {
        root = new Node(false);
    }
    
    /** Inserts a word into the trie. */
    public void Insert(string word) {        
        Node temp = root;
        for(int i = 0; i < word.Length; i++){
            int value = Convert.ToInt32(word[i]) - 97;
            
            if(temp.values[value] == null){
                temp.values[value] = new Node(false);
            }
            
            temp = temp.values[value];
        }
        temp.isEnd = true;
    }
    
    /** Returns if the word is in the trie. */
    public bool Search(string word) {
        Node temp = root;   
        
        for(int i = 0; i < word.Length; i++){
            int value = Convert.ToInt32(word[i]) - 97;
            
            if(temp == null || temp.values[value] == null){
                return false;
            }
            
            temp = temp.values[value];
        }
        
        return temp.isEnd;
    }
    
    /** Returns if there is any word in the trie that starts with the given prefix. */
    public bool StartsWith(string prefix) {
        Node temp = root;   
        
        for(int i = 0; i < prefix.Length; i++){
            int value = Convert.ToInt32(prefix[i]) - 97;
            
            if(temp == null || temp.values[value] == null){
                return false;
            }
            
            temp = temp.values[value];
        }
        
        return true;
    }
}
```
