---
title: Word Search II
date: "2020-07-01"
type: problem-solving
description: Word Search II
tags: csharp
---

Note: This problem was taken from LeetCode - [Word Search II](https://leetcode.com/problems/word-search-ii/)

### Using Trie and DFS

```csharp
public class Solution {
    public IList<string> FindWords(char[][] board, string[] words) {
        List<string> output = new List<string>();
        
        int rows = board.Length;
        if(rows == 0){
            return output;
        }
        int cols = board[0].Length;
        
        TrieNode root = this.BuildTrie(words);
        
        for(int i = 0; i < rows; i++){
            for(int j = 0; j < cols; j++){
                this.DFS(board, root, i, j, output, rows, cols);
            }
        }
        
        return output;
    }
    
    public void DFS(char[][] board, TrieNode root, int r, int c, List<string> output, int rows, int cols){
        char ch = board[r][c];
        
        if(ch == '#' || root.next[ch-'a'] == null){
            return;
        }
        
        root = root.next[ch-'a'];
        
        if(root.word != null){
            output.Add(root.word);
            root.word = null;
        }
        
        board[r][c] = '#';
        
        if(r > 0){
            this.DFS(board, root, r-1, c, output, rows, cols);
        }
        if(c > 0){
            this.DFS(board, root, r, c-1, output, rows, cols);   
        }
        if(r < rows-1){
            this.DFS(board, root, r+1, c, output, rows, cols);
        }
        if(c < cols-1){
            this.DFS(board, root, r, c+1, output, rows, cols);
        }
        board[r][c] = ch;
        
    }
    
    public TrieNode BuildTrie(string[] words){
        TrieNode root = new TrieNode();
        
        foreach(string w in words){
            TrieNode tempNode = root;
            
            foreach(char c in w){
                int i = c - 'a';
                
                if(tempNode.next[i] == null){
                    tempNode.next[i] = new TrieNode();
                }
                
                tempNode = tempNode.next[i];
            }
            tempNode.word = w;
        }
        return root;
    }
    
}


public class TrieNode{
    public String word;
    public TrieNode[] next = new TrieNode[26];
}
```
