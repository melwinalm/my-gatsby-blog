---
title: Pascal's Triangle
date: "2020-03-10"
type: problem-solving
description: Pascal's Triangle
tags: csharp
---

Note: This problem was taken from LeetCode - [Pascal's Triangle](https://leetcode.com/problems/pascals-triangle/)



```csharp
public IList<IList<int>> Generate(int numRows) {
    IList<IList<int>> output = new List<IList<int>>();
    
    if(numRows == 0){
        return output;
    }
    if (numRows >=1){
        output.Add(new List<int> {1});
    }
    if (numRows >= 2){
        output.Add(new List<int>{1,1});
    }
      
    List<int> temp = new List<int>() {1,1};
    
    for(int i = 3; i <= numRows; i++){
        List<int> temp2 = new List<int>();
        
        temp2.Add(1);
        
        for(int j = 1; j < temp.Count; j++){
            temp2.Add(temp[j-1] + temp[j]);
        }
        
        temp2.Add(1);
        output.Add(temp2);
        temp = temp2;
    }
    
    return output;
}
```
