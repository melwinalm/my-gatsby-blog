---
title: Design Circular Queue
date: "2021-04-05"
type: problem-solving
description: Design Circular Queue
tags: csharp
---

Note: This problem was taken from LeetCode - [Design Circular Queue](https://leetcode.com/problems/design-circular-queue/)

### Using List

```csharp
public class MyCircularQueue {
    int[] data;
    int fPtr;
    int rPtr;
    int len;
    
    public MyCircularQueue(int k) {
        data = new int[k];
        fPtr = 0;
        rPtr = -1;
        len = 0;
    }
    
    public bool EnQueue(int value) {
        if(!this.IsFull()){
            rPtr = (rPtr + 1) % data.Length;
            data[rPtr] = value;
            len++;
            return true;
        }
        else{
            return false;
        }
    }
    
    public bool DeQueue() {
        if(!this.IsEmpty()){
            fPtr = (fPtr + 1) % data.Length;
            len--;
            return true;
        }
        else{
            return false;
        }
    }
    
    public int Front() {
        return this.IsEmpty() ? -1 : data[fPtr];
    }
    
    public int Rear() {
        return this.IsEmpty() ? -1 : data[rPtr];
    }
    
    public bool IsEmpty() {
        return len == 0;
    }
        
    public bool IsFull() {
        return len == data.Length;
    }
}
```
