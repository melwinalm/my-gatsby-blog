---
title: Valid Parentheses
date: "2020-01-21"
type: problem-solving
description: Valid Parentheses
tags: csharp
---

Note: This problem was taken from LeetCode - [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)

This problem can be solved using the Stack data structure. Start by looping through each character in the string array. Push it to the stack when there is an opening parenthesis and pop an element from the stack and see if it a matching parenthesis. Keep repeating this to get the result.

```csharp
public bool IsValid(string s) {
    Stack<char> chars = new Stack<char>();
    
    // Dictionary to store the opening and closing parenthesis groups
    Dictionary<char,char> dict = new Dictionary<char,char>();
    dict['{'] = '}';
    dict['('] = ')';
    dict['['] = ']';
    
    for(int i = 0; i< s.Length; i++){
        if(s[i] == '(' || s[i] == '[' || s[i] == '{'){
            chars.Push(s[i]);
        }
        else{
            // Checks if the stack is empty before popping an element out of the stack 
            if(chars.Count == 0){
                return false;
            }    
            char temp = chars.Pop();
            if(dict[temp] != s[i]){
                return false;
            }
        }
    }
    return chars.Count == 0;
}
```

The above solution has time complexity and space complexity of O(n).
