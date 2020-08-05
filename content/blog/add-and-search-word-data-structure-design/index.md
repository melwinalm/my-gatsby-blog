---
title: Add and Search Word - Data structure design
date: "2020-05-08"
type: problem-solving
description: Add and Search Word - Data structure design
tags: csharp
---

Note: This problem was taken from LeetCode - [Add and Search Word - Data structure design](https://leetcode.com/problems/add-and-search-word-data-structure-design/)

### Using Depth First Approach

```csharp
public class WordDictionary {
    public TrieNode rootNode;
    
    public WordDictionary() {
        rootNode = new TrieNode(true);
    }

    public void AddWord(string word) {
        TrieNode temp = rootNode;
        
        for(int i = 0; i < word.Length; i++){
            int asciiValue = Convert.ToInt32(word[i]) - 96;
            
            if(temp.nodes[asciiValue] == null){
                temp.nodes[asciiValue] = new TrieNode(false);
            }
            temp = temp.nodes[asciiValue];
        }
        temp.val = true;
    }
    
    public bool Search(string word) {
        TrieNode temp = rootNode;  
        return this.Search(word, 0, temp);
    }
    
    private bool Search(string word, int currIndex, TrieNode temp){
        if(currIndex == word.Length){
            return temp.val;
        }
        
        int asciiValue = Convert.ToInt32(word[currIndex]) - 96;
        if(word[currIndex] != '.'){
            return temp.nodes[asciiValue] != null && this.Search(word, currIndex + 1, temp.nodes[asciiValue]);
        }
        else{
            for(int i = 0; i < temp.nodes.Length; i++){
                if(temp.nodes[i] != null && this.Search(word, currIndex + 1, temp.nodes[i])){
                    return true;
                }
            }
        }
        
        return false;
    }
}

public class TrieNode{
    public bool val;
    public TrieNode[] nodes;
    
    public TrieNode(bool _val){
        this.val = _val;
        this.nodes = new TrieNode[27];
    }
}
```

### Using Breadth First Approach

```csharp
public class WordDictionary {

    Trie root;
    public WordDictionary() {
        root = new Trie();
    }

    public void AddWord(string word) {
        Trie tempNode = root;
        foreach(char c in word){
            int charValue = c - 'a';
            
            if(tempNode.child[charValue] == null){
                tempNode.child[charValue] = new Trie();
            }
            tempNode = tempNode.child[charValue];
        }
        tempNode.isWord = true;
    }

    public bool Search(string word) {
        Queue<Trie> bfsQueue = new Queue<Trie>();
        bfsQueue.Enqueue(root);
        
        foreach(char c in word){
            int count = bfsQueue.Count;
            
            if(c == '.'){
                for(int i = 0; i < count; i++){
                    Trie tempNode = bfsQueue.Dequeue();
                    
                    for(int j = 0; j < tempNode.child.Length; j++){
                        if(tempNode.child[j] != null){
                            bfsQueue.Enqueue(tempNode.child[j]);
                        }
                    }
                    
                }
            }
            else{
                for(int i = 0; i < count; i++){
                    int charValue = c - 'a';
                    Trie tempNode = bfsQueue.Dequeue();
                    
                    if(tempNode.child[charValue] != null){
                        bfsQueue.Enqueue(tempNode.child[charValue]);
                    }
                
                }
            }
        }
        
        while(bfsQueue.Count > 0){
            if(bfsQueue.Dequeue().isWord == true){
                return true;
            }
        }
        
        return false;
    }
}

public class Trie{
    public Trie[] child;
    public bool isWord;
    
    public Trie(){
        child = new Trie[26];
        isWord = false;
    }
}
```
