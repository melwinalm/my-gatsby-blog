---
title: Min Stack
date: "2020-06-16"
type: problem-solving
description: Min Stack
tags: csharp
---

Note: This problem was taken from LeetCode - [Min Stack](https://leetcode.com/problems/min-stack/)

### Using Two Stacks

```csharp
public class MinStack {
    Stack<int> mainStack = new Stack<int>();
    Stack<int> minStack = new Stack<int>();
    
    public MinStack() {
        mainStack = new Stack<int>();
        minStack = new Stack<int>();    
    }
    
    public void Push(int x) {
        mainStack.Push(x);
        
        // Whenever the value to pushed is less than the top element then push the new element. Else push the new element. 
        if(minStack.Count == 0 || x < minStack.Peek()){
            minStack.Push(x);
        }
        else{
            minStack.Push(minStack.Peek());
        }
    }
    
    public void Pop() {
        mainStack.Pop();
        minStack.Pop();
    }
    
    public int Top() {
        return mainStack.Peek();
    }
    
    public int GetMin() {
        return minStack.Peek();
    }
}
```
