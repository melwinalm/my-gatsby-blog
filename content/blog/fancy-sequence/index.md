---
title: Fancy Sequence
date: "2020-10-18"
type: problem-solving
description: Fancy Sequence
tags: csharp
---

Note: This problem was taken from LeetCode - [Fancy Sequence](https://leetcode.com/problems/fancy-sequence/)

### Naive Solution - Pre-Computated (Time Limit Exceeded Error)

```csharp
public class Fancy {
    List<long> lst;
    
    public Fancy() {
        lst = new List<long>();
    }
    
    public void Append(int val) {
        lst.Add(val);
    }
    
    public void AddAll(int inc) {
        for(int i = 0; i < lst.Count; i++){
            lst[i] %= 1000000007;
            lst[i] += inc;
        }
    }
    
    public void MultAll(int m) {
        for(int i = 0; i < lst.Count; i++){
            lst[i] %= 1000000007;
            lst[i] *= m;
        }
    }
    
    public int GetIndex(int idx) {
        if(idx >= lst.Count){
            return -1;
        }
        
        return (int)(lst[idx] % 1000000007);
    }
}
```

### Naive Solution - Post-Computed (Lazy Propogation) (Time Limit Exceeded Error)

```csharp
public class Fancy {
    List<long> lst;
    List<Tuple<int, char, int>> ops;
    
    public Fancy() {
        lst = new List<long>();
        ops = new List<Tuple<int, char, int>>();
    }
    
    public void Append(int val) {
        lst.Add(val);
    }
    
    public void AddAll(int inc) {
        ops.Add(new Tuple<int, char, int>(lst.Count - 1, 'a', inc));
    }
    
    public void MultAll(int m) {
        ops.Add(new Tuple<int, char, int>(lst.Count - 1, 'm', m));
    }
    
    public int GetIndex(int idx) {
        if(idx >= lst.Count){
            return -1;
        }
        
        long val = lst[idx];
        
        foreach(var item in ops){
            if(item.Item1 < idx){
                continue;
            }
            
            val %= 1000000007;
            
            if(item.Item2 == 'a'){
                val += item.Item3;
            }
            else{
                val *= item.Item3;
            }
        }
        
        return (int)(val % 1000000007);
    }
}
```

### Prefix Sum

To be solved
