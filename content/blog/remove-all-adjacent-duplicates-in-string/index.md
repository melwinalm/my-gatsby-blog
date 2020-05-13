---
title: Remove All Adjacent Duplicates In String
date: "2020-05-13"
type: problem-solving
description: Remove All Adjacent Duplicates In String
tags: csharp
---

Note: This problem was taken from LeetCode - [Remove All Adjacent Duplicates In String](https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string/)

### Using Stack

```csharp
    public string RemoveDuplicates(string S) {
        
        Stack<char> temp = new Stack<char>();
        
        for(int i = 0; i < S.Length; i++){
			// If stack is empty then push the character to the stack
            if(temp.Count == 0){
                temp.Push(S[i]);
            }
            else{
				// Peek and check if the current character is the same. If yes then Pop it out of the stack, else Push it to the stack 
                if(temp.Peek() == S[i]){
                    temp.Pop();
                }
                else{
                    temp.Push(S[i]);
                }
            }
        }
        
        StringBuilder output = new StringBuilder();
        
        while(temp.Count > 0){
            output.Insert(0, temp.Pop());
        }
        
        return output.ToString();
    }
```
