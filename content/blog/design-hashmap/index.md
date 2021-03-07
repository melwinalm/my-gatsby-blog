---
title: Design HashMap
date: "2021-03-07"
type: problem-solving
description: Design HashMap
tags: csharp
---

Note: This problem was taken from LeetCode - [Design HashMap](https://leetcode.com/problems/design-hashmap/)

### Using Array

```csharp
public class MyHashMap {

    int[] store;
    
    public MyHashMap() {
        store = new int[1000001];
        Array.Fill(store, -1);
    }
    
    public void Put(int key, int value) {
        store[key] = value;
    }
    
    public int Get(int key) {
        return store[key];
    }
    
    public void Remove(int key) {
        store[key] = -1;
    }
}

```
