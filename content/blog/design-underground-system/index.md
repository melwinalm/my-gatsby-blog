---
title: Design Underground System
date: "2021-03-21"
type: problem-solving
description: Design Underground System
tags: csharp
---

Note: This problem was taken from LeetCode - [Design Underground System](https://leetcode.com/problems/design-underground-system/)

```csharp
public class UndergroundSystem {

    Dictionary<int, Tuple<string, int>> checkInDict;
    Dictionary<string, Tuple<int, int>> checkOutDict;
    
    public UndergroundSystem() {
        checkInDict = new Dictionary<int, Tuple<string, int>>();
        checkOutDict = new Dictionary<string, Tuple<int, int>>();
    }
    
    public void CheckIn(int id, string stationName, int t) {
        checkInDict[id] = new Tuple<string, int>(stationName, t);
    }
    
    public void CheckOut(int id, string stationName, int t) {
        Tuple<string, int> temp = checkInDict[id];
        string route = temp.Item1 + "$" + stationName;
        int totalTime = t - temp.Item2;
        
        Tuple<int, int> checkOut;
        if(!checkOutDict.ContainsKey(route)){
            checkOutDict[route] = new Tuple<int, int>(0, 0);
        }
        
        int routeTotalTime = checkOutDict[route].Item1 + totalTime;
        int totalRoutes = checkOutDict[route].Item2 + 1;
        
        checkOutDict[route] = new Tuple<int, int>(routeTotalTime, totalRoutes);
    }
    
    public double GetAverageTime(string startStation, string endStation) {
        string route = startStation + "$" + endStation;
        Tuple<int, int> checkout = checkOutDict[route];
        return (double) checkout.Item1 / (double)checkout.Item2;
    }
}
```
