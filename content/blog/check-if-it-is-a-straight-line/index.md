---
title: Check If It Is a Straight Line
date: "2020-03-06"
type: problem-solving
description: Check If It Is a Straight Line
tags: csharp
---

Note: This problem was taken from LeetCode - [Check If It Is a Straight Line](https://leetcode.com/problems/check-if-it-is-a-straight-line/)

To find if a given set of points on a plane form a straight line use the standard equation, i.e `y = mx + c` where x, y are the coordinates, m is the slope of the line and c is constant. Applying this on two coordinates we get `m = (y2 - y1)/(x2 - x1)` which is `m = dy/dx`. For a set of points to form a straight line, the slope should remain the same so, apply this condition to all the remaining coordinates to see if the slope is the same. Use this equation `(y - y1)/(x - x1) = dy/dx` which is `dx(y - y1) =  dy(x - x1)`.

```csharp
public bool CheckStraightLine(int[][] coordinates) {
    if(coordinates.Length <= 2){
        return true;
    }

    int x1 = coordinates[0][0];
    int y1 = coordinates[0][1];
    int x2 = coordinates[1][0];
    int y2 = coordinates[1][1];
    
    int dx = x2 - x1;
    int dy = y2 - y1;
    
    for(int i = 2; i < coordinates.Length; i++){
        int x = coordinates[i][0];
        int y = coordinates[i][1];
        
        if(dx * (y - y1) != dy * (x - x1)){
            return false;
        }
    }
    
    return true;
}
```
