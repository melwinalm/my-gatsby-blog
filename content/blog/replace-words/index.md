---
title: Replace Words
date: "2020-09-02"
type: problem-solving
description: Replace Words
tags: csharp
---

Note: This problem was taken from LeetCode - [Replace Words](https://leetcode.com/problems/replace-words/)

### Using Trie

```csharp
public class Solution {
    public string ReplaceWords(IList<string> dictionary, string sentence) {
        Trie root = new Trie();
        
        // Build Trie
        foreach(string word in dictionary){
            Trie tempNode = root;

            foreach(char c in word){
                int charValue = c - 'a';
                
                if(tempNode.children[charValue] == null){
                    tempNode.children[charValue] = new Trie();
                }
                
                tempNode = tempNode.children[charValue];
            }
            
            tempNode.isWord = true;
        }
        
        string[] words = sentence.Split(' ');
        
        for(int i = 0; i < words.Length; i++){
            Trie tempNode = root;
            
            string appendString = "";
            
            foreach(char c in words[i]){
                int charValue = c - 'a';
                
                if(tempNode.isWord){
                    words[i] = appendString;
                    break;
                }
                
                if(tempNode.children[charValue] == null){
                    break;
                }
                
                tempNode = tempNode.children[charValue];
                
                appendString += c;
            }
        }
        
        return string.Join(" ", words);
    }
}

public class Trie{
    public Trie[] children;
    public bool isWord;
    
    public Trie(){
        children = new Trie[26];
        isWord = false;
    }
}
```
