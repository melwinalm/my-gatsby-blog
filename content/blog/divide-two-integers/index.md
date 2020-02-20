---
title: Divide Two Integers
date: "2020-02-13"
type: problem-solving
description: Divide Two Integers
tags: csharp
---

Note: This problem was taken from LeetCode - [Divide Two Integers](https://leetcode.com/problems/divide-two-integers/)

### Repeated Subtraction

Repeatedly subtract the dividend by the divisor and update the counter each time. The `isPositive` flag is used to check if the quotient is going to be positive or negative and based on this flag the `count` is incremented or decremented each time.

```csharp
public int Divide(int dividend, int divisor) {
    int count = 0;
    int tempDividend = Math.Abs(dividend);
    int tempDivisor = Math.Abs(divisor);
    
    bool isPositive = false;
    
    if((tempDividend == dividend && tempDivisor == divisor) || (tempDividend != dividend && tempDivisor != divisor)){
        isPositive = true;
    }
    
    while(tempDividend - tempDivisor >= 0){
        tempDividend = tempDividend - tempDivisor;
        
        if(isPositive){
            count++;
        }
        else{
            count--;
        }
    }
    return count;
}
```
