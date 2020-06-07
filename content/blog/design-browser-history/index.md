---
title: Design Browser History
date: "2020-06-07"
type: problem-solving
description: Design Browser History
tags: csharp
---

Note: This problem was taken from LeetCode - [Design Browser History](https://leetcode.com/problems/design-browser-history/)

### Using Dynamic List

```csharp
public class BrowserHistory {
    List<string> UrlList;
    int pointer;
    int maxForwardPointer;
	
    public BrowserHistory(string homepage) {
        UrlList = new List<string>();
        pointer = 0;
        maxForwardPointer = 0;
        UrlList.Add(homepage);
    }
    
    public void Visit(string url) {
        pointer++;
        maxForwardPointer = pointer;
        if(UrlList.Count > pointer){
            UrlList[pointer] = url;
        }
        else{
            UrlList.Add(url);
        }
    }
    
    public string Back(int steps) {
        pointer = Math.Max(0, pointer - steps);
        return UrlList[pointer];
    }
    
    public string Forward(int steps) {  
        pointer = Math.Min(maxForwardPointer, pointer + steps);
        return UrlList[pointer];
    }
}
```
