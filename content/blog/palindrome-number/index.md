---
title: Palindrome Number
date: "2020-01-23"
type: problem-solving
description: Palindrome Number
tags: csharp
---

Note: This problem was taken from LeetCode - [Palindrome Number](https://leetcode.com/problems/palindrome-number/)

### Naive Approach

The naive way to solve this problem would be to convert the given number to a string and then reverse it. Then compare if the original string and the reversed strings are the same. 

See the next approach which doesn't involve converting the number to a string.

### Better Approach

First, check if the number is negative since a negative number cannot be a palindrome. Now, get the mod 10 of the number, this gives your the last digit, then multiply it by 10. Divide the input number by 10 which will remove the last digit. Keep repeating this. In the end, check if the input number and the reversed one are the same. 

```csharp
public bool IsPalindrome(int x) {
    // Checks if the given number is negative
    if(x < 0){
        return false;
    }
    
    int original = x;
    int reverse = 0;
    while(x != 0){
        reverse = (x % 10) + (reverse * 10);
        x /= 10;
    }
    
    if(original == reverse){
        return true;
    }
    return false;
}
```
