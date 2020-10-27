---
title: Basic Calculator
date: "2020-10-28"
type: problem-solving
description: Basic Calculator
tags: csharp
---

Note: This problem was taken from LeetCode - [Basic Calculator](https://leetcode.com/problems/basic-calculator/)

### Using Stack

```csharp
public class Solution {
    public int Calculate(string s) {
        Stack<string> stack = new Stack<string>();
        
        int i = 0;
        while(i < s.Length){
            if(s[i] == ' '){
                i++;
                continue;
            }
            
            if(s[i] != ')'){
                stack.Push(s[i].ToString());
            }
            else{
                List<string> eval = new List<string>();
                
                while(stack.Peek() != "("){
                    eval.Insert(0, stack.Pop());
                }
                
                stack.Pop();
                stack.Push(this.Evaluate(eval));
            }
            
            i++;
        }
                
        List<string> eval2 = new List<string>();
        while(stack.Count > 0){
            if(stack.Peek() == "("){
                stack.Pop();
                continue;
            }
            
            eval2.Insert(0, stack.Pop());
        }

        return Convert.ToInt32(this.Evaluate(eval2));
    }
    
    public string Evaluate(List<string> s){
        int tempEval = 0;
        bool isPlus = true;
        
        string nextNum = "";
        
        for(int i = 0; i < s.Count; i++){
            if(s[i] == "+" || s[i] == "-"){
                tempEval = isPlus ? tempEval + Convert.ToInt32(nextNum) : tempEval - Convert.ToInt32(nextNum);
                isPlus = s[i] == "+" ? true : false;
                
                nextNum = "";
            }
            else{
                nextNum += s[i];                
            }
        }
        
        tempEval = isPlus ? tempEval + Convert.ToInt32(nextNum) : tempEval - Convert.ToInt32(nextNum);
        
        return tempEval.ToString();
    }
}
```
