---
title: Roman to Integer
date: "2020-03-10"
type: problem-solving
description: Roman to Integer
tags: csharp
---

Note: This problem was taken from LeetCode - [Roman to Integer](https://leetcode.com/problems/roman-to-integer/)

Create a map table which has key and values of roman numbers and its corresponding integer value. Now loop through the given roman number input. If you find that the value of the previous character is greater than the current one, then add it to the result. Else subtract the previous num value. Keep doing this until the end of the input to get the integer value.

Consider the following examples

- `VIII` - Here `V`(prevNum) is greater than `I`(currNum) so add it to the result.
- `IV` - Here `I`(prevNum) is lesser than `V` so subtract from the result. 

```csharp
public int RomanToInt(string s) {
    Dictionary<char,int> MAP = new Dictionary<char,int>();
    
    MAP['I'] = 1;
    MAP['V'] = 5;
    MAP['X'] = 10;
    MAP['L'] = 50;
    MAP['C'] = 100;
    MAP['D'] = 500;
    MAP['M'] = 1000;
    
    int  preNum = 0;
    int result = 0;
    
    for(int i = 0; i < s.Length; i++){
        int currNum = MAP[s[i]];
        
        if(preNum >= currNum){
            result += currNum;
        }
        else{
            // preNum needs to be deducted twice since it has been added already in the previous iteration
            result = result - (2 * preNum) + currNum;
        }
        preNum = currNum;
    }
    
    return result;
}
```
