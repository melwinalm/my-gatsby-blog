---
title: Reverse Integer
date: "2020-03-09"
type: problem-solving
description: Reverse Integer
tags: csharp
---

Note: This problem was taken from LeetCode - [Reverse Integer](https://leetcode.com/problems/reverse-integer/)

This is a typical reverse a number problem. Simply mod the given number by 10. That gives you the last digit of the number then divide the input number by 10. That will remove the last digit of the number. Keep doing this to get the reversed number. To find if the number overflows, put the output in `long` datatype and check if the number is same as the int datatype.

```csharp
public int Reverse(int x) {
    long output = 0;
    
    while(x != 0){
        int temp = x % 10;
        output = (output * 10) + temp;
        x /= 10;
    }
    
    if((int)output != output){
        return 0;
    }
    
    return (int)output;
}
```
