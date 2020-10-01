---
title: Number of Recent Calls
date: "2020-09-01"
type: problem-solving
description: Number of Recent Calls
tags: csharp
---

Note: This problem was taken from LeetCode - [Number of Recent Calls](https://leetcode.com/problems/number-of-recent-calls/)

### Using Queue

```csharp
public class RecentCounter {
    Queue<int> myQ;
    public RecentCounter() {
        myQ = new Queue<int>();
    }
    
    public int Ping(int t) {
        myQ.Enqueue(t);
        
        while(myQ.Peek() < t-3000){
            myQ.Dequeue();
        }
        
        return myQ.Count;
    }
}
```
