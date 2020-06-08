---
title: Design Linked List
date: "2020-06-08"
type: problem-solving
description: Design Linked List
tags: csharp
---

Note: This problem was taken from LeetCode - [Design Linked List](https://leetcode.com/problems/design-linked-list/)

### Using Dynamic List

```csharp
public class MyLinkedList {
    List<int> values;
    int tailIndex;

    public MyLinkedList() {
        values = new List<int>();
        tailIndex = -1;
    }
    
    public int Get(int index) {
        if(index <= tailIndex){
            return values[index];
        }
        else{
            return -1;
        }
    }
    
    public void AddAtHead(int val) {
        values.Insert(0, val);
        tailIndex++;
    }
    
    public void AddAtTail(int val) {
        values.Add(val);
        tailIndex++;
    }
    
    public void AddAtIndex(int index, int val) {
        if(index <= tailIndex + 1){
            values.Insert(index, val);
            tailIndex++;
        }
    }
    
    public void DeleteAtIndex(int index) {
        if(index <= tailIndex){
            values.RemoveAt(index);
            tailIndex--;
        }
    }
}
```
