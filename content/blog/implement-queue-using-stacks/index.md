---
title: Implement Queue using Stacks
date: "2020-03-19"
type: problem-solving
description: Implement Queue using Stacks
tags: csharp
---

Note: This problem was taken from LeetCode - [Implement Queue using Stacks](https://leetcode.com/problems/implement-queue-using-stacks/)

### O(1) Push and O(N) Pop time Approach

This approach requires two stacks. 

During the `Enqueue` operation push the element straight into the `main` stack. 

During the `Dequeue` operation, check if the `sub` stack has any items. If the `sub` stack has items then `pop` it straight away and return. If it's empty then `pop` all the items from the `main` stack and put it into the `sub` stack and then `pop` the element from the `sub` stack and return.

`Peek` operation is similar to the `Pop`.

And for the `Empty` method check the lengths of both the stacks.

```csharp
public class MyQueue {

    Stack<int> main;
    Stack<int> sub;
    /** Initialize your data structure here. */
    public MyQueue() {
        main = new Stack<int>();
        sub = new Stack<int>();
    }
    
    /** Push element x to the back of queue. */
    // Enqueue Operation
    public void Push(int x) {
        main.Push(x);
    }
    
    /** Removes the element from in front of queue and returns that element. */
    // Dequeue Operation
    public int Pop() {
        if(sub.Count == 0){
            while(main.Count != 0){
                sub.Push(main.Pop());
            }
        }
        if(sub.Count == 0){
            return - 1;
        }
        else{
            return sub.Pop();
        }
    }
    
    /** Get the front element. */
    public int Peek() {
        if(sub.Count == 0){
            while(main.Count != 0){
                sub.Push(main.Pop());
            }
        }
        if(sub.Count == 0){
            return - 1;
        }
        else{
            return sub.Peek();
        }
    }
    
    /** Returns whether the queue is empty. */
    public bool Empty() {
        return main.Count == 0 && sub.Count == 0;
    }
}
```
