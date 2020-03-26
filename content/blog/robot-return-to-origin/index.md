---
title: Robot Return to Origin
date: "2020-03-23"
type: problem-solving
description: Robot Return to Origin
tags: csharp
---

Note: This problem was taken from LeetCode - [Robot Return to Origin](https://leetcode.com/problems/robot-return-to-origin/)

Maintain two counters one for vertical and another for horizontal moves. Iterate over all the moves in the given input. Increment or decrement these counter values as you iterate through the `moves` array. In the end, if both the counter values are zero then it means that the robot has returned to the origin.

```csharp
public bool JudgeCircle(string moves) {
    int xCount = 0;
    int yCount = 0;
    
    for(int i = 0; i < moves.Length; i++){
        switch(moves[i]){
            case 'L': 
                xCount -= 1; break;
            case 'R':
                xCount += 1; break;
            case 'U':
                yCount -= 1; break;
            case 'D':
                yCount += 1; break;
        }
    }
    
    return xCount == 0 && yCount == 0;
}
```
