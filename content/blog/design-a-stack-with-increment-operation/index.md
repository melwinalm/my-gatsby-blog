---
title: Design a Stack With Increment Operation
date: "2020-05-13"
type: problem-solving
description: Design a Stack With Increment Operation
tags: csharp
---

Note: This problem was taken from LeetCode - [Design a Stack With Increment Operation](https://leetcode.com/problems/design-a-stack-with-increment-operation/)

### Using Static Array

```csharp
public class CustomStack {
    int[] list;
    int currentPointer;
    int max;
    public CustomStack(int maxSize) {
        list = new int[maxSize];
        currentPointer = 0;
        this.max = maxSize;
    }
    
    public void Push(int x) {
        if(currentPointer == max){
            return;
        }
        else{
            list[currentPointer] = x;
            currentPointer++;
        }
    }
    
    public int Pop() {
        if(currentPointer == 0){
            return -1;
        }
        else{
            currentPointer--;
            return list[currentPointer];
        }
    }
    
    public void Increment(int k, int val) {
        int maxPointer = Math.Min(k, currentPointer);
        
        for(int i = 0; i < maxPointer; i++){
            Console.WriteLine(i.ToString());
            list[i] = list[i] + val;
        }
    }
}
```
