---
title: Convert Binary Number in a Linked List to Integer
date: "2020-03-06"
type: problem-solving
description: Convert Binary Number in a Linked List to Integer
tags: csharp
---

Note: This problem was taken from LeetCode - [Convert Binary Number in a Linked List to Integer](https://leetcode.com/problems/convert-binary-number-in-a-linked-list-to-integer/)

A binary number can be converted to decimal using this - `((2^0) * 1st bit) + ((2^1) * 2nd bit) ...... (2^(n-1) * nth bit)`. Use this to find the decimal value.

```csharp
public int GetDecimalValue(ListNode head) {
    if(head == null){
        return 0;
    }   
    
    int num = 0;
    
    while(head != null){
        num = (2 * num) + head.val;
        head = head.next;
    }
    
    return num;
}
```
