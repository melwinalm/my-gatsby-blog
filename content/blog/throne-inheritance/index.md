---
title: Throne Inheritance
date: "2020-09-27"
type: problem-solving
description: Throne Inheritance
tags: csharp
---

Note: This problem was taken from LeetCode - [Throne Inheritance](https://leetcode.com/problems/throne-inheritance/)

### Using Dictionary and DFS

```csharp
public class ThroneInheritance {

    string king;
    Dictionary<string, List<string>> map;
    HashSet<string> dead;
    
    public ThroneInheritance(string kingName) {
        this.king = kingName;
        map = new Dictionary<string, List<string>>();
        dead = new HashSet<string>();
    }
    
    public void Birth(string parentName, string childName) {
        if(!map.ContainsKey(parentName)){
            map[parentName] = new List<string>();
        }
        
        map[parentName].Add(childName);
    }
    
    public void Death(string name) {
        dead.Add(name);
    }
    
    public IList<string> GetInheritanceOrder() {
        List<string> list = this.GetList(king);
        List<string> output = new List<string>();
        
        foreach(string item in list){
            if(!dead.Contains(item)){
                output.Add(item);
            }
        }
        
        return output;
    }
    
    public List<string> GetList(string parent){
        List<string> res = new List<string>();
        res.Add(parent);
        
        if(!map.ContainsKey(parent)){
            map[parent] = new List<string>();
        }
        
        foreach(string child in map[parent]){
            res.AddRange(this.GetList(child));
        }
        
        return res;
    }
}
```
